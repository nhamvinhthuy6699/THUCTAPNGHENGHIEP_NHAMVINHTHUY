## CẤU HÌNH CÀI ĐẶT MOODLE ĐỂ TẢI SEB LÊN MÁY

### Cài Moodle 4.5.12 trên Ubuntu bằng Apache + PHP 8.3-FPM + MariaDB

## 1. Khai báo thông tin ban đầu

```
PROTOCOL="http://"
read -p "Nhap IP hoac domain Moodle, vi du 192.168.18.8 hoac moodle.local: " WEBSITE_ADDRESS

MOODLE_PATH="/var/www/html/sites"
MOODLE_CODE_FOLDER="$MOODLE_PATH/moodle"
MOODLE_DATA_FOLDER="/var/www/data"

sudo mkdir -p "$MOODLE_PATH"
sudo mkdir -p "$MOODLE_DATA_FOLDER"
```

## 2. Cập nhật Ubuntu

```
sudo apt-get update && sudo apt-get upgrade -y
```

## 3. Cài các gói hỗ trợ cơ bản

```
sudo apt-get install -y software-properties-common ca-certificates lsb-release apt-transport-https curl wget unzip git nano openssl
```

## 4. Cài PHP 8.3 và extension cho Moodle

### Nếu dùng Ubuntu 22.04

Ubuntu 22.04 thường không có sẵn PHP 8.3, nên cần thêm repo PHP 8.3 trước:

```
sudo add-apt-repository ppa:ondrej/php -y
sudo apt-get update
```

### Cài PHP 8.3

```
sudo apt-get install -y \
php8.3-fpm php8.3-cli php8.3-curl php8.3-zip php8.3-gd php8.3-xml \
php8.3-intl php8.3-mbstring php8.3-soap php8.3-bcmath \
php8.3-ldap php8.3-mysql php8.3-opcache php8.3-readline php8.3-sodium
```

Kiểm tra PHP:

```
php -v
```

---

## 5. Cài MariaDB và gói hỗ trợ Moodle

```
sudo apt-get install -y \
mariadb-server mariadb-client graphviz aspell git clamav ghostscript composer wget curl openssl
```

Bật MariaDB:

```
sudo systemctl enable --now mariadb
```

Kiểm tra MariaDB:

```
sudo systemctl status mariadb
```

---

## 6. Cài Apache làm Webserver

Tài liệu Moodle có 2 lựa chọn là Apache hoặc Nginx. Ở đây chọn **Option 1: Apache**, không cài Nginx.

```
sudo apt-get install -y apache2 libapache2-mod-fcgid
```

Bật module Apache cần thiết:

```
sudo a2enmod proxy_fcgi setenvif rewrite
```

Bật PHP-FPM:

```
sudo systemctl enable --now php8.3-fpm
```

Kiểm tra PHP-FPM:

```
sudo systemctl status php8.3-fpm
```

---

## 7. Tải Moodle 4.5.12 bằng Git

```
sudo git clone -b v4.5.12 https://github.com/moodle/moodle.git "$MOODLE_CODE_FOLDER"
```

Phân quyền:

```
sudo chown -R www-data:www-data "$MOODLE_CODE_FOLDER"
cd "$MOODLE_CODE_FOLDER"
```

Kiểm tra source Moodle:

```
ls
```

Với Moodle 4.5.12, cần thấy các file/thư mục như:

```
admin
auth
course
index.php
install.php
lib
login
mod
theme
version.php
```

## 8. Cài thư viện PHP bằng Composer

```
CACHE_DIR="/var/www/.cache/composer"

sudo mkdir -p "$CACHE_DIR"
sudo chown -R www-data:www-data "$CACHE_DIR"
sudo chmod -R 750 "$CACHE_DIR"

sudo -u www-data COMPOSER_CACHE_DIR="$CACHE_DIR" composer install --no-dev --classmap-authoritative
```

Phân quyền lại:

```
sudo chown -R www-data:www-data "$MOODLE_CODE_FOLDER"
sudo find "$MOODLE_CODE_FOLDER" -type d -exec chmod 755 {} \;
sudo find "$MOODLE_CODE_FOLDER" -type f -exec chmod 644 {} \;
```

## 9. Tạo thư mục moodledata

```
sudo mkdir -p "$MOODLE_DATA_FOLDER/moodledata"
sudo chown -R www-data:www-data "$MOODLE_DATA_FOLDER/moodledata"
sudo chmod 700 "$MOODLE_DATA_FOLDER/moodledata"
```

Kiểm tra:

```
ls -ld "$MOODLE_DATA_FOLDER/moodledata"
```


## 10. Tạo cấu hình Apache cho Moodle

Vì Moodle 4.5.12 không có thư mục `public`, `DocumentRoot` phải trỏ thẳng vào:

```text
/var/www/html/sites/moodle
```

Tạo file cấu hình Apache:

```
sudo tee /etc/apache2/sites-available/moodle.conf > /dev/null <<EOF
<VirtualHost *:80>
    ServerName $WEBSITE_ADDRESS

    DocumentRoot $MOODLE_CODE_FOLDER

    <Directory $MOODLE_CODE_FOLDER>
        Options FollowSymLinks
        AllowOverride None
        Require all granted
        DirectoryIndex index.php index.html
    </Directory>

    <FilesMatch "\\.php$">
        SetHandler "proxy:unix:/run/php/php8.3-fpm.sock|fcgi://localhost/"
    </FilesMatch>

    ErrorLog \${APACHE_LOG_DIR}/moodle_error.log
    CustomLog \${APACHE_LOG_DIR}/moodle_access.log combined
</VirtualHost>
EOF
```

Bật site Moodle và tắt site mặc định:

```
sudo a2ensite moodle.conf
sudo a2dissite 000-default.conf
```

Kiểm tra Apache:

```
sudo apache2ctl configtest
```

Restart Apache và PHP-FPM:

```
sudo systemctl restart apache2
sudo systemctl restart php8.3-fpm
```


## 11. Chỉnh PHP 8.3 cho Moodle

```
php_ini_fpm="/etc/php/8.3/fpm/php.ini"
php_ini_cli="/etc/php/8.3/cli/php.ini"

sudo sed -i 's/^[[:space:]]*;*[[:space:]]*max_input_vars[[:space:]]*=.*/max_input_vars = 5000/' "$php_ini_fpm"
sudo sed -i 's/^[[:space:]]*;*[[:space:]]*max_input_vars[[:space:]]*=.*/max_input_vars = 5000/' "$php_ini_cli"

sudo sed -i 's/^\s*post_max_size\s*=.*/post_max_size = 256M/' "$php_ini_fpm"
sudo sed -i 's/^\s*post_max_size\s*=.*/post_max_size = 256M/' "$php_ini_cli"

sudo sed -i 's/^\s*upload_max_filesize\s*=.*/upload_max_filesize = 256M/' "$php_ini_fpm"
sudo sed -i 's/^\s*upload_max_filesize\s*=.*/upload_max_filesize = 256M/' "$php_ini_cli"

sudo sed -i 's/^\s*memory_limit\s*=.*/memory_limit = 512M/' "$php_ini_fpm"
sudo sed -i 's/^\s*memory_limit\s*=.*/memory_limit = 512M/' "$php_ini_cli"

sudo sed -i 's/^\s*max_execution_time\s*=.*/max_execution_time = 300/' "$php_ini_fpm"
sudo sed -i 's/^\s*max_execution_time\s*=.*/max_execution_time = 300/' "$php_ini_cli"

sudo systemctl reload php8.3-fpm
sudo systemctl restart apache2
```

## 12. Tạo database cho Moodle

Đặt mật khẩu database:

```
MYSQL_MOODLEUSER_PASSWORD="123"
```

Tạo database:

```
sudo mysql -e "CREATE DATABASE moodle DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
```

Tạo user:

```
sudo mysql -e "CREATE USER 'moodleuser'@'localhost' IDENTIFIED BY '$MYSQL_MOODLEUSER_PASSWORD';"
```

Cấp quyền:

```
sudo mysql -e "GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, CREATE TEMPORARY TABLES, DROP, INDEX, ALTER ON moodle.* TO 'moodleuser'@'localhost';"
```

Áp dụng quyền:

```
sudo mysql -e "FLUSH PRIVILEGES;"
```


## 13. Cài Moodle bằng giao diện web

Mở trình duyệt và truy cập:

```
http://IPADDRESSES
```

Khi Moodle hỏi đường dẫn, nhập:

```text
Web address: http://IPCUABAN
Moodle directory: /var/www/html/sites/moodle
Data directory: /var/www/data/moodledata
```

## 14. Tạo cron cho Moodle

Sau khi cài xong Moodle, tạo cron cho user `www-data`:

```
echo "* * * * * /usr/bin/php /var/www/html/sites/moodle/admin/cli/cron.php >/dev/null" | sudo crontab -u www-data -
```

Kiểm tra cron:

```
sudo -u www-data php /var/www/html/sites/moodle/admin/cli/cron.php
```


## 15. Kiểm tra dịch vụ

Kiểm tra Apache:

```
sudo systemctl status apache2
```

Kiểm tra PHP-FPM:

```
sudo systemctl status php8.3-fpm
```

Kiểm tra MariaDB:

```
sudo systemctl status mariadb
```

Kiểm tra PHP:

```
php -v
```

Kiểm tra extension PHP:

```
php -m | grep -E "curl|zip|gd|xml|intl|mbstring|soap|bcmath|ldap|mysql|sodium|opcache"
```

Xem log Apache nếu lỗi:

```
sudo tail -n 50 /var/log/apache2/moodle_error.log
```

---

# OPTION 2: CÀI NGINX LÀM WEBSERVER

Nếu chọn **Nginx** thì không chạy phần **Option 1: Apache**.
Nếu trước đó đã cài Apache rồi thì cần dừng Apache để Nginx dùng được cổng `80`.

## 1. Cài Nginx làm Webserver

Tài liệu Moodle có 2 lựa chọn là Apache hoặc Nginx. Ở đây chọn **Option 2: Nginx**, không cần cài Apache.

```
sudo apt-get install -y nginx
```

Bật Nginx:

```
sudo systemctl enable --now nginx
```

Kiểm tra Nginx:

```
sudo systemctl status nginx
```

---

## 2. Nếu trước đó đã lỡ cài Apache

Nếu máy đã từng cài Apache, cần dừng Apache để tránh bị chiếm cổng `80`.

```
sudo systemctl stop apache2
sudo systemctl disable apache2
```

Kiểm tra cổng `80`:

```
sudo ss -tulnp | grep :80
```

Nếu thấy `nginx` là đúng:

```
users:(("nginx",pid=...,fd=...))
```

Nếu vẫn thấy `apache2`, chạy lại:

```
sudo systemctl stop apache2
sudo systemctl disable apache2
sudo systemctl restart nginx
```

---

## 3. Tạo cấu hình Nginx cho Moodle

Vì Moodle 4.5.12 không có thư mục `public`, `root` phải trỏ thẳng vào:

```text
/var/www/html/sites/moodle
```

Tạo file cấu hình Nginx:

```
sudo tee /etc/nginx/sites-available/moodle.conf > /dev/null <<EOF
server {
    listen 80;
    server_name $WEBSITE_ADDRESS www.$WEBSITE_ADDRESS;

    root $MOODLE_CODE_FOLDER;
    index index.php index.html index.htm;

    client_max_body_size 256M;

    location / {
        try_files \$uri \$uri/ /index.php?\$args;
    }

    location ~ [^/]\.php(/|$) {
        fastcgi_split_path_info ^(.+\.php)(/.+)\$;
        fastcgi_index index.php;

        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME \$document_root\$fastcgi_script_name;
        fastcgi_param PATH_INFO \$fastcgi_path_info;

        fastcgi_pass unix:/run/php/php8.3-fpm.sock;
    }

    location ~ /\. {
        deny all;
    }

    location ~* /(?:config\.php|composer\.json|composer\.lock|README|readme|UPGRADING|phpunit\.xml|behat\.yml) {
        deny all;
    }

    location ~* /(vendor|node_modules|tests|cache|localcache|temp|sessions)/ {
        deny all;
    }

    error_log /var/log/nginx/moodle_error.log;
    access_log /var/log/nginx/moodle_access.log;
}
EOF
```
## 4. Bật site Moodle trên Nginx

Tạo liên kết site:

```
sudo ln -sf /etc/nginx/sites-available/moodle.conf /etc/nginx/sites-enabled/moodle.conf
```

Tắt site mặc định của Nginx:

```
sudo rm -f /etc/nginx/sites-enabled/default
```

Kiểm tra cấu hình Nginx:

```
sudo nginx -t
```

Restart Nginx và PHP-FPM:

```
sudo systemctl restart nginx
sudo systemctl restart php8.3-fpm
```

## 5. Kiểm tra Nginx đang chạy cổng 80

```
sudo ss -tulnp | grep :80
```

Kết quả đúng là thấy `nginx`:

```text
users:(("nginx",pid=...,fd=...))
```
## 6. Kiểm tra dịch vụ nếu dùng Nginx

Kiểm tra Nginx:

```
sudo systemctl status nginx
```

Kiểm tra PHP-FPM:

```
sudo systemctl status php8.3-fpm
```

Kiểm tra MariaDB:

```
sudo systemctl status mariadb
```

Kiểm tra PHP:

```
php -v
```

Kiểm tra extension PHP:

```
php -m | grep -E "curl|zip|gd|xml|intl|mbstring|soap|bcmath|ldap|mysql|sodium|opcache"
```

Xem log Nginx nếu lỗi:

```
sudo tail -n 50 /var/log/nginx/moodle_error.log
```

Xem log PHP-FPM nếu lỗi:

```
sudo journalctl -u php8.3-fpm -n 50
```
