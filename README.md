# vcs-fitcycle-install

## Management Server

Ubuntu 18.04 Latest
1. Add Team Authorization Keys
2. Hosts File
3. Create RSA Key
4. MySQL Client insatll
    sudo apt-get install mysql-client -y
5. Wavefront Install
6. Fluentd Install

# DB1 Server - Please use the VCS-CTS default username and password (Ask Sean)

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config Mysql
    sudo apt-get install mysql-client mysql-server -y
    ## Update Bind Address in Mysql Config
        sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
            Update bind-address 0.0.0.0
    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Create and assign permissions Prospect DB
        CREATE DATABASE prospect;
        use prospect;
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'abc123';
        GRANT ALL PRIVILEGES ON *.* TO 'db_user'@'%' IDENTIFIED BY 'abc123';
        CREATE USER 'haproxy_check'@'%';
        FLUSH PRIVILEGES;
        Quit;
    ## Restore Prospect DB
        sudo mysql -u root -p prospect < prospect_backup.sql
    ## Restart Mysql Service
        sudo systemctl restart mysql.service

# DB2 Server - Please use the VCS-CTS default username and password (Ask Sean)

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config Mysql
    sudo apt-get install mysql-client mysql-server -y
    ## Update Bind Address in Mysql Config
        sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
            Update bind-address 0.0.0.0
    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Create and assign permissions Prospect DB
        CREATE DATABASE prospect;
        use prospect;
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'abc123';
        GRANT ALL PRIVILEGES ON *.* TO 'db_user'@'%' IDENTIFIED BY 'abc123';
        CREATE USER 'haproxy_check'@'%';
        FLUSH PRIVILEGES;
        Quit;
    ## Restore Prospect DB
        sudo mysql -u root -p prospect < prospect_backup.sql
    ## Restart Mysql Service
        sudo systemctl restart mysql.service

# DBLB Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config HAProxy
    sudo apt-get install haproxy -y
    replace /etc/haproxy/haproxy.cfg with config_files/haproxy.cfg
    haproxy -c -f /etc/haproxy/haproxy.cfg
    sudo service haproxy restart
3. Wavefront Install
4. Fluentd Install

#### Test Remote connectivity to MySQL Servers (Directly and via HAproxy)

mysql -u db_app_user -h db1 -p
mysql -u db_app_user -h db2 -p
mysql -u db_app_user -h dblb -p

# APP1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-fitcycle
3. Wavefront Install
4. Fluentd Install

# APP2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-fitcycle
3. Wavefront Install
4. Fluentd Install

# API1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-apiserver
3. Wavefront Install
4. Fluentd Install

# API2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-apiserver
3. Wavefront Install
4. Fluentd Install

# WEB1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config HAProxy
    sudo apt-get install nginx -y
    replace /etc/nginx/nginx.conf with config_files/nginx.conf
    sudo systemctl restart nginx
3. Wavefront Install
4. Fluentd Install
5. Install bash script to create nginx stop cron job
    wget https://github.com/theseanodell/vcs-fitcycle-install/raw/master/generatecron/generatenginxcron
    sudo chmod +x generatenginxcron
    sudo mv generatenginxcron /etc/cron.daily
    

# WEB2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config HAProxy
    sudo apt-get install nginx -y
    replace /etc/nginx/nginx.conf with config_files/nginx.conf
    sudo systemctl restart nginx
3. Wavefront Install
4. Fluentd Install
