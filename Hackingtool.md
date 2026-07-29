# CÀI ĐẶT MÔI TRƯỜNG HACKINGTOOL TRÊN UBUNTU

## 1. Cài các thành phần cần thiết

```bash
sudo apt update
sudo apt install -y git python3 python3-pip python3-venv
```

Kiểm tra:

```bash
python3 --version
git --version
```

HackingTool yêu cầu Python từ phiên bản `3.10` trở lên.

---

## 2. Tải mã nguồn

```bash
mkdir -p ~/hacking-lab
cd ~/hacking-lab

git clone https://github.com/Z4nzu/hackingtool.git
cd hackingtool
```

Kiểm tra commit hiện tại:

```bash
git log -1 --oneline
git rev-parse HEAD
```

```text
01a51bbca6d0c7a20696aeef9ed92b143e26b10c
```

---

## 3. Tạo môi trường Python ảo

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Kiểm tra:

```bash
which python
which pip
```

Đường dẫn phải nằm trong:

```text
~/hacking-lab/hackingtool/.venv/
```

---

## 4. Cài thư viện Python

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

---

## 6. Chạy lại môi trường vào lần sau

```bash
cd ~/hacking-lab/hackingtool
source .venv/bin/activate
```

Thoát môi trường:

```bash
deactivate
```
