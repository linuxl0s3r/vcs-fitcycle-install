# vcs-fitcycle-install

## Management Server

Ubuntu 18.04 Latest
1. Add Team Authorization Keys
2. Hosts File
3. Create RSA Key
    ## Run command
        ssh-keygen -b 4096
4. MySQL Client install
    ## Run command
        sudo apt-get update && sudo apt-get install mysql-client -y && sudo apt-get update && sudo apt-get upgrade -y
5. Wavefront Install
6. Fluentd Setup/Config
    ## Install td-agent
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Install fluent-plugin-http-ext   
        sudo /usr/sbin/td-agent-gem install fluent-plugin-out-http-ext
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    ##### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# DB1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config Mysql
    ## Run command
        sudo apt-get install mysql-client mysql-server -y && sudo apt-get update && sudo apt-get upgrade -y
    ## Update Bind Address in Mysql Config
        sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf

    #### *Update bind-address 0.0.0.0*

    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Create users and passwords (CHANGE Identified by fields with default passwords)
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'VMware1!';
        GRANT ALL PRIVILEGES ON *.* TO 'db_app_user'@'%' IDENTIFIED BY 'VMware1!';
        CREATE USER 'haproxy_check'@'%';
        FLUSH PRIVILEGES;
    ## Create Prospect DB
        CREATE DATABASE prospect;
        Quit;
    ## Restore Prospect DB
        sudo mysql -u root -p prospect < prospect_backup.sql
    ## Restart Mysql Service
        sudo systemctl restart mysql.service
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# DB2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config Mysql
    ## Run command
        sudo apt-get install mysql-client mysql-server -y && sudo apt-get update && sudo apt-get upgrade -y
    ## Update Bind Address in Mysql Config
        sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf

    #### *Update bind-address 0.0.0.0*

    ## Connect to Mysql
        sudo mysql -u root -p -h localhost
    ## Create users and passwords (CHANGE Identified by fields with default passwords)
        ALTER USER 'root'@'localhost' IDENTIFIED BY 'abc123';
        GRANT ALL PRIVILEGES ON *.* TO 'db_app_user'@'%' IDENTIFIED BY 'abc123';
        CREATE USER 'haproxy_check'@'%';
        FLUSH PRIVILEGES;
    ## Create Prospect DB
        CREATE DATABASE prospect;
        Quit;
    ## Restore Prospect DB
        sudo mysql -u root -p prospect < prospect_backup.sql
    ## Restart Mysql Service
        sudo systemctl restart mysql.service
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# DBLB Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config HAProxy
    ## Install
        sudo apt-get install haproxy -y && sudo apt-get update && sudo apt-get upgrade -y

    #### *Replace /etc/haproxy/haproxy.cfg with config_files/haproxy.cfg*

    ## HAproxy Config Validation
        haproxy -c -f /etc/haproxy/haproxy.cfg
    ## Service Restart
        sudo service haproxy restart
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

##### Test Remote connectivity to MySQL Servers (Directly and via HAproxy)

``mysql -u db_app_user -h db1 -p``
``mysql -u db_app_user -h db2 -p``
``mysql -u db_app_user -h dblb -p``

# APP1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-fitcycle
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# APP2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-fitcycle
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# API1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-apiserver
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# API2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Follow steps in readme: https://github.com/theseanodell/vcs-apiserver
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

# WEB1 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config NGINX
        sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install nginx -y && sudo apt-get update && sudo apt-get upgrade -y

    #### *Replace /etc/nginx/nginx.conf with config_files/nginx.conf*

        sudo systemctl restart nginx
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent


# WEB2 Server

Ubuntu 18.04 Latest
1. Hosts File
2. Install/Config NGINX
        sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install nginx -y && sudo apt-get update && sudo apt-get upgrade -y

    #### *Replace /etc/nginx/nginx.conf with config_files/nginx.conf*

        sudo systemctl restart nginx
3. Wavefront Install
4. Fluentd Setup/Config
    ## Install
        sudo curl -L https://toolbelt.treasuredata.com/sh/install-ubuntu-bionic-td-agent3.sh | sh
    ## Update Config File
        Navigate to https://github.com/theseanodell/vcs-fitcycle-fluentd

    #### *Copy and Update config file with necessary parameters - see readme in repo*

    ## Restart tdagent
        sudo systemctl restart td-agent

##### Problem Modifications

# Web1

1. Break Web NGINX
Create cron jobs for Nginx
    ## Installs and configures Cron jobs for Nginx stop / start for WF.
        wget https://github.com/theseanodell/vcs-fitcycle-install/raw/master/generatecron/generatenginxcron
        sudo chmod +x generatenginxcron
        sudo mv generatenginxcron /etc/cron.daily
2.


###### Hosted MySQL on Azure

1. Allow Azure Resource Connectivity
2. Install/Config Mysql
    ## Connect to Mysql
          sudo mysql -u "db_user" -p -h "db_instance"
    ## Create users and passwords (CHANGE Identified by fields with default passwords)
          CREATE USER 'haproxy_check'@'%';
          CREATE USER 'db_app_user'@'%' IDENTIFIED BY 'VMware1!';
          GRANT ALL PRIVILEGES ON prospect . * TO 'db_app_user'@'%';
          FLUSH PRIVILEGES;
    ## Create Prospect DB
          CREATE DATABASE prospect;
          Quit;
    ## Restore Prospect DB
          sudo mysql -u "db_user" -p -h "db_instance" prospect < prospect_backup.sql

###### Hosted MySQL on AWS RDS
1. Setup and Configure RDS Instance
2. Config MySQL
    ## Connect to Mysql
          sudo mysql -u "db_user" -p -h "db_instance"
    ## Create users and passwords (CHANGE Identified by fields with default passwords)
          CREATE USER 'haproxy_check'@'%';
          CREATE USER 'db_app_user'@'%' IDENTIFIED BY 'VMware1!';
          GRANT ALL PRIVILEGES ON prospect . * TO 'db_app_user'@'%';
          FLUSH PRIVILEGES;
    ## Restore Prospect DB
          sudo mysql -h "db_instance" -u db_app_user -p prospect < prospect_backup.sql
