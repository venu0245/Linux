## MANAGING SERVICES:

* init services:
.start
.stop
.restart
.reload

* some service didn't 
 .chkconfig on,off

* check the crond services 
 ```
 .systemctl status crond.services
 .systemctl enable --now crond.services
 ```

* To start the service
 ```
 .systemctl start crond.services
 ```   

* To stop and reload the services
 ```
 .systemctl stop crond.services
 .systemctl reload crond.services
 ```

#### FIREWALL:


* systemctl status firewall
 ```
  firewall status 
  firewall-cmd --state
  firewall-cmd --list-all
 ```

 * To add FTP,HTTP,TCP in firewall 
 ```
 .firewall-cmd --add-services=ftp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all
 ```
 ```
 .firewall-cmd --add-services=tcp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all
 ```

* To add the ports numbers
  ```
  .firewall-cmd --add-port=2222/ftp --permanent
  .firewall-cmd --reload
  .firewall-cmd --list-all 
  ```
  ```
* To remove the services
```
   .firewall-cmd --remove-service=tcp   --permanent 
   .firewall-cmd --reload
   .firewall-cmd --list-all
  ``` 

* To remove the ports of the services
 ```
 .firewall-cmd --remove-port=2222/tcp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all
 ```

* check the service which port number works on 
 
 for example:
 .cockpit.socket
 ```
 .systemctl status cockpit.socket
 .systemctl enable cockpit.socket --now
 .systemctl status cockpit.socket
 ```

* To check the server which port  works on it
   .https://xxxxxxxx:9090