## WEB SERVER

*  package : httpd
*  port : 80,443
*  sample configuration file : /usr/share/doc/httpd/httpd-vhost.conf
*  configuration file : /etc/httpd/conf/httpd.conf
                     : /etc/httpd/conf.d/ssl.conf
*  configuration directory : /etc/httpd/conf.d
*  document root : /var/www/html
*  daemon : htttpd
### lab-setup

* ```
  dnf install httpd* -y  
  ``` 
  ![preview](images/web.PNG)

* ```
  systemctl status httpd
  systemctl enable --now httpd
  systemctl reload httpd 
  firewall-cmd --list-all
  firewall-cmd --add-service=httpd --permanent
  firewall-cmd --list-reload
  firewall-cmd --list-all
  ```   
  ![preview](images/web1.PNG)
  ![preview](images/web2.PNG)
  ![preview](images/web3.PNG)
* after add fireall and service,we can check on any brower
  ```
  http://192.168.10.60
  ```  

* create a own website 
  
  ```
  . cd /var/www/html
  . vim index.html
  ```

* create a web page in index.html and also altimalate configure in main file

  ![preview](images/web4.PNG)

* copying the sample configuration file into main configuration file directory called as 'vsw.conf'

  ```
  .  cp /usr/share/doc/httpd/httpd-vhosts.conf /etc/httpd/conf.d/vsw.conf
  ```

* vim /etc/httpd/conf.d/vsw.conf   
  ![preview](images/web5.PNG)

* create a new web pages with `Alias-names`
* create a directory name called as pg2 in /var/www/html in

  ```
  .cd /var/www/html
  .index.html pg2
  .cd pg2
  .vim index.html
  ```
  ![preview](images/web6.PNG)

  ```
  vim /etc/httpd/conf.d/vsw.conf
  ```
  ![preview](images/web7.PNG)  
  ![preview](images/web8.PNG)
* and also open website with index.html `redirect` http://www.gmail.com

  ![preview](images/web9.PNG)
   
   ```
    <VirtualHost 192.168.10.60:80>
    ServerAdmin root@venu60.git.com
    DocumentRoot "/var/www/html"
    Alias /venu  "/var/www/html/web"
    Redirect /red "https://www.github.com"
    ServerName venu60.git.com
    ErrorLog "/var/log/httpd/vnu-error_log"
    CustomLog "/var/log/httpd/vnu-access_log" common
     </VirtualHost>
   ```
* Redirect means we can add any webste with own alias names
  
* Only working rhel terminal in firefox brower  
  
  ```
  cd /var/wwww/html
   index.html
  ```
### PORT BASED WEBHOSTING

* ```
  cd /var/www
  ls
  html
  ```
* create a directory with name as `port`
  ```
  mkdir port
  cp html/index.html/port
  cd port
  vim index.html
    <h1>Port based network </h1>
  ```  
* create a new separate configuration file 
  
  ```
  cp /etc/httpd/conf.d/wed.conf /etc/httpd/conf.d/app.conf
  cd /etc/httpd/conf.d/
  ls
  cp web.conf app.conf
  ```  
  `192.168.10.60:8080` 
  
  ```
  Listen 8080
  <VirtualHost 192.168.10.60:8080>
    ServerAdmin root@venu60.git.com
    DocumentRoot "/var/www/port"
    ServerName venu60.git.com
    ErrorLog "/var/log/httpd/web-error_log"
    CustomLog "/var/log/httpd/web-access_log" common
   </VirtualHost>
  ```
  ![preview](images/web11.PNG)
  ```
  firewall-cmd --add-port=8080 --permanent
  firewall-cmd --reload
  firewall-cmd --list-all
  systemctl reload httpd.service
  ```
* check which port number are specified 
  ```netstat -ntlp |grep -i httpd
  ```






  
