## WEB SERVER

* package : httpd
* port : 80,443
* sample configuration file : /usr/share/doc/httpd/httpd-vhost.conf
* configuration file : /etc/httpd/conf/httpd.conf
                     : /etc/httpd/conf.d/ssl.conf
* configuration directory : /etc/httpd/conf.d
* document root : /var/www/html
* daemon : htttpd
### lab-setup

* ```
  dnf install httpd* -y  
  ``` 
  ![preview](images/web.PNG)

* ```
  systemctl status httpd
  systemctl enable --now httpd 
  firewall-cmd --list-all
  firewall-cmd --add-service=httpd --permanent
  firewall-cmd --list-reload
  firewall-cmd --list-all
  ```
  ![preview](images/web1.PNG)
  ![preview](images/web2.PNG)
  ![preview](images/web3.PNG)

* create a own website 
  
  ```
  . cd /var/www/html
  . vim index.html
  ```
  ![preview](images/web4.PNG)

* copying the sample configuration file into main configuration file directory

  ```
  .  cp /usr/share/doc/httpd/httpd-vhosts.conf /etc/httpd/conf.d/vsw.conf
  ```

* vim /etc/httpd/conf.d/vsw.conf   








  
