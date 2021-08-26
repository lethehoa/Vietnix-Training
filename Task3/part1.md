# Task 3
## Content
---
1. <a href="#1">Reverse proxy (nginx)</a>
2. <a href="#2">Remote mysql</a>
3. <a href="#3">vsftpd</a>
4. <a href="#4">phpmyadmin</a>
5. <a href="#5">Build wordpress webiste, allow remote mysql and vsftpd</a>
6. <a href="#6">Virtual Host Apaches</a>

---
<div id="1"></div>

## Reverse proxy (nginx)

![topology nginx](./img/reverse-proxy-nginx-topology.jpg)

>A Nginx HTTPS reverse proxy is an intermediary proxy service which takes a client request, passes it on to one or more servers, and subsequently delivers the server's response back to the client.

### 1. Download required software: Apache, nginx

```bash
sudo apt-get install apache2
```
```bash
sudo apt-get install nginx
```

- Start Apache
```bash
sudo service apache2 start
```
- In browser, type your machine's ip address, you will see default Apache website.
- Open **Developer tool** and check Response Headers, you'll see Server of this website is **Apache**.
![check header before](./img/prove_apach.png)

### 2. Configuration
- Change default Apache's port

In **/etc/apache2/sites-available/000-default.conf**, change default port in the first line to 8080 (whatever port you want).
![Change default port](./img/changport_000.png)

In **/etc/apache2/ports.conf**, change default port in the first line to 8080 (whatever port you want).
![Change default port](./img/change_ports.png)

Access website through port 8080
![new port](./img/change_port_apache.png)

- Configure nginx

In **/etc/nginx/sites-available/defaul**, add those lines (from 52 --> 56) and comment line 51. Change to your IP address in line 52.
![nginx configure](./img/change_nginx.png)

Restart nginx
```bash
sudo service nginx restart
```

Access website again, in this time, you don't need to specify port number.

Open **Developer tool**, nd check Response Headers, you'll see Server of this website is **nginx**.

![prove nginx](./img/nginx_prove.png)

---
<div id="2"></div>

## Remote mysql

- Install mysql
```bash
sudo apt-get install mariadb-server
```
I used mariadb because my distro only support **mariadb**, feel free to change to **sudo apt-get install mysql-server** if your distro support it.

- Configure mysql

> By default mysql doesn't allow remote login by root user, so we need to configure those things.

In **/etc/mysql/mariadb.conf.d/50-server.cnf**, comment line **bind-address**
![set up bind address mysql](./img/setup_mysql_remote.jpeg)


Create new user and grant privileges for it.
![create new user](./img/create_user_to_remote_mysql.jpeg)
> Feel free to use your own user

![importain user setup](./img/required_setup.jpeg)

After that, restart mysql
```bash
sudo service mariadb restart
```

- Remote login with your user credential that you created.

![login successful](./img/login_remote_success.jpeg)

---
<div id="3"><div>

## vsftpd
> vsftpd, is an FTP server for Unix-like systems, including Linux.

- Install vsftpd
```bash
sudo apt-get install vsftpd
```
Start **vsftpd**
![start_vsftpd](./img/start_vsftpd.jpeg) 

- Using **FileZilla** to connect to vsftpd server (through port 21).

![connect vsftpd](./img/test_file_vsftpd.jpeg)

---
<div id="4"></div>

## phpmyadmin
> phpMyAdmin is a free and open source administration tool for MySQL and MariaDB.
- Install phpmyadmin
```bash
sudo apt-get install myphpadmin
```
![install phpmyadmin](./img/install_phpmyadmin.jpeg)

While installing, you'll be ask for set up some basic information (database, password)

![setup phpmyadmin](./img/setup_phpmyadmin.jpeg)
![setup phpmyadmin](./img/setup_password_phpmyadin.jpeg)
Type your own password

- Go to **\<your IP address>/phpmyadmin** to access myphpadmin dashboard.

You'll be ask to login, use user that you created in mariadb.
![phpadmin dashboard](./img/phpadmin-dashboard.png)

---
<div id="5"></div>

## 5. Configure wordpress

> Setup and configure database, apache like first section of [this part](./Task2/part1.md)

> Make sure to keep **nginx** running as a reverse proxy like the first section of this part.

---

## 6. Virtual Host Apache

> Virtual hosting is a method for **hosting multiple domain names on a single server**. This allows one server to share its resources, such as memory and processor cycles, without requiring all services provided to use the same host name.

- In **/etc/apache2/sites-availble** copy file config. I create two virtual hosts here, so I copied two files.
![copy config file](./img/copy-file.png) 

- Change content of each file, change your **server name, server alias and document root (point to your web folder).
![change content file](./img/change-configfile.png)
![change content file](./img/change-confilefile1.png)

- Enable new config file and disable old config file (this step means **link new files** and **unlink old file** to those files in **etc/apache2/sites-enable**, you can use symbolic command, I use another command here but the purpose is the same).
![link new file, unlink old file](./img/enable-config-file.png)

- Result (If you run server on Virtual Machine and access through local machine, you have to point those domains to server's IP on file **hosts**).
![result](./img/final-result.png)

