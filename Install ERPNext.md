
# 1- Install WSL

1- افتح **PowerShell كمسؤول** (Run as Administrator)، ثم نفّذ الأمر التالي:

```powershaell
wsl --install
```

2- ثم اكتب
```powershell
ubuntu
```

----

# 2- Open terminal than to ubuntu


**Update ubuntu**

```bash
sudo apt update -y && sudo apt upgrade -y && sudo apt full-upgrade -y && sudo apt autoclean -y && sudo apt autoremove -y
```

## install python 3.10

```bash
sudo apt install software-properties-common -y
sudo add-apt-repository ppa:deadsnakes/ppa -y
sudo apt update
sudo apt install python3.10 python3.10-dev python3.10-venv -y
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
sudo update-alternatives --config python3
curl -sS https://bootstrap.pypa.io/get-pip.py | sudo python3.10
python3.10 -m pip --version
sudo ln -sf /usr/bin/python3.10 /usr/bin/python
sudo ln -sf /usr/local/bin/pip /usr/bin/pip
```

## تثبيت المتطلبات الأساسية

```bash
sudo apt install git python3.10-dev python3.10-venv python3-pip redis-server libmariadb-dev mariadb-server mariadb-client pkg-config
```

### 1. ادخل إلى MariaDB باستخدام **sudo**:


```bash
sudo mariadb
```

إذا دخلت وظهر لك:


`MariaDB [(none)]>`

فأنت داخل النظام كـ root بنجاح.

---

### 2. غيّر طريقة التوثيق لحساب root إلى `mysql_native_password` لتقدر تستخدمه لاحقًا بكلمة مرور:



```bash
USE mysql;  ALTER USER 'root'@'localhost' IDENTIFIED VIA mysql_native_password USING PASSWORD('your_new_password');  FLUSH PRIVILEGES; EXIT;
```

✅ استبدل `your_new_password` بكلمة مرور قوية.


## بعدها

```bash
sudo mariadb-secure-installation
```

## راح يسألك جاوب ب Y/N  بعدها 


```bash
nano /etc/mysql/my.cnf
```
**And add this configuration in end file**

```bash
[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

[mysql]
default-character-set = utf8mb4
```
**restart MariaDB**
```bash
sudo systemctl restart mariadb
```

----

## **Install Node**
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

```

```Bash
nvm install 18
```

**Close Terminal than**

```bash
npm install -g yarn
```

```bash
sudo apt install xvfb libfontconfig

```
------

## تثبيت bench (أداة إدارة ERPNext):

```bash
sudo pip install frappe-bench
```

## إنشاء مجلد مشروع:

```bash
mkdir ~/frappe-bench && cd ~/frappe-bench
bench init --frappe-branch version-15 frappe

```

## إنشاء موقع جديد:

```bash
cd frappe
bench new-site erp.localhost

```

🗝️ سيسألك عن:

- كلمة مرور مدير قاعدة البيانات (MariaDB root)
    
- وكلمة مرور مدير ERPNext (Administrator)


## تثبيت ERPNext التطبيق نفسه:

```bash
bench get-app --branch version-15 erpnext
bench --site erp.localhost install-app erpnext
```

## تشغيل السيرفر:


```bash
bench start
```

- ثم افتح المتصفح على:


```bash
http://localhost:8000
```


