# Frappe-guide
sudo service cron start
sudo service redis-server start
sudo service mysql start




Frappe guide

Init bench

Normal init : bench init --frappe-branch version-13 nanma-crm

Get app: bench get-app https://github.com/ALAN-KREISE/nanma-crm.git –branch dev1

Create site: bench new-site nanma.localhost

Install app: bench --site nanma.localhost install-app nanma_app

Restore: bench --site nanma.localhost restore ./apps/nanma_app/backups/20220721_113003-nanma_crm-database.sql.gz

bench set-config -g developer_mode true

Docker :  bench init --skip-redis-config-generation --frappe-branch version-13 --python python3.9 nitta-approval

—--------------------------------------------------------------------------------------------------------
Ubuntu config(without ui (wsl))

First, shutdown wsl and confirm the name.
wsl --shutdown
wsl --list --verbose

  NAME            STATE           VERSION
* Ubuntu-20.04    Stopped         2
Then you can export the tar file and import it to D drive:
mkdir d:\backuplinux
wsl --export Ubuntu-20.04 d:\backuplinux\ubuntu.tar
wsl --unregister Ubuntu-20.04
mkdir d:\wsl
wsl --import Ubuntu-20.04 d:\wsl\ d:\backuplinux\ubuntu.tar
ubuntu2004.exe config --default-user yourloginname
Check d:\wsl, the ext4 file is moved here. Also check the free space on your C drive. You should see a big difference.

Ubuntu folder on windows : opt/frappe
Username: ideen
Pass: ideen



Frappe full installation steps:

*install python 3.7

sudo apt -y update
sudo apt -y install software-properties-common dirmngr apt-transport-https lsb-release ca-certificates

sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.7

*install nvm and node

sudo apt install curl 
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 
source ~/.profile 
nvm install node 

*To install a specific version of node:

nvm install 14

 

sudo add-apt-repository ppa:redislabs/redis
sudo apt update
sudo apt install redis-server
sudo systemctl restart redis.service || sudo service redis-server start
redis-cli

*install mariadb 10.3

sudo apt-get install mariadb-server-10.3
mysql_secure_installation
sudo mysql -u root -p

use mysql;
set password for 'root'@'localhost' = password('root');
flush privileges;
quit

sudo apt-get install mariadb-client-10.3
nano /etc/mysql/my.cnf

[mysqld]
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

[mysql]
default-character-set = utf8mb4

sudo service mysql restart

*install yarn

npm install -g yarn

*install pip

sudo apt install python3-pip

sudo apt-get install xvfb libfontconfig wkhtmltopdf

*install cron

apt install cron
systemctl enable --now cron

*install frappe
sudo pip3 install frappe-bench
bench --version






Add-ons

sudo service --status-all
if no systemctl
sudo service redis-server start
sudo service redis-server status
ALTER USER root@localhost IDENTIFIED VIA mysql_native_password;
SET PASSWORD = PASSWORD('asvignesh');
FLUSH PRIVILEGES;  mariadb access denied for root@localhost (edited)
