# Install Odoo 17 on Ubuntu 20.04

## Cập nhật Server
<code>sudo apt-get update </code> <br>
<code>sudo apt-get upgrade </code> <br>

## Tải Packages và Thư viện
<code>sudo apt-get install -y python3-pip </code> <br> <br>
Tải thêm các gói phụ thuộc cho Odoo: <br> <br>
<code>sudo apt-get install python-dev python3-dev libxml2-dev libxslt1-dev zlib1g-dev libsasl2-dev libldap2-dev build-essential libssl-dev libffi-dev libmysqlclient-dev libjpeg-dev libpq-dev libjpeg8-dev liblcms2-dev libblas-dev libatlas-base-dev <br>
sudo apt-get install -y npm <br>
sudo ln -s /usr/bin/nodejs /usr/bin/node <br>
sudo npm install -g less less-plugin-clean-css <br>
sudo apt-get install -y node-less <br>
</code>

## Cài đặt Postgresql
sudo apt-get install postgresql <br>

### Tạo user odoo17 và phân quyền superuser <br>
sudo su - postgres
createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo17

psql <br>
ALTER USER odoo17 WITH SUPERUSER; <br>
\q <br>
exit <br>

## Tạo user system và thư mục cho user system
sudo adduser --system --home=/opt/odoo17 --group odoo17 <br>

## Cài đặt git và clone odoo17 từ user system
sudo apt-get install git <br>
sudo su - odoo17 -s /bin/bash <br>
git clone https://www.github.com/odoo/odoo --depth 1 --branch 17.0 --single-branch . <br>

## Cài đặt các packages python cần thiết
sudo pip3 install -r /opt/odoo/requirements.txt <br>

## Cài đặt Wkhtmltopdf chuyển đổi từ html sang pdf
sudo wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.bionic_amd64.deb <br>
sudo dpkg -i wkhtmltox_0.12.5-1.bionic_amd64.deb <br>
sudo apt install -f <br>
