MANAGING SERVICES:
-----------------

* init services:
.start
.stop
.restart
.reload

* some service didn't 
 .chkconfig on,off

* check the services 
 .systemctl status crond.services
 .systemctl is-active crond.services

* To start the service
 .systemctl start crond.services  

* To stop the services
.systemctl stop crond.services

* To reload the services
 .systemctl reload crond.services

FIREWALL:
---------

* systemctl status firewall

* firewall status 
 .firewall-cmd --state
 .firewall-cmd --list-all

 * To add FTP,HTTP,TCP in firewall we use 
  
  .firewall-cmd --add-services=ftp --permanent

* after add the service we can reload the service
 .firewall-cmd --reload
 .firewall-cmd --list-all

 .firewall-cmd --add-services=tcp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all

* To add the ports for specific services
 .firewall-cmd --add-port=2222/ftp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all 

* To remove the services
  .firewall-cmd --add-remove=tcp --permanent 
  .firewall-cmd --reload
  .firewall-cmd --list-all

* To remove the ports of the services
 .firewall-cmd --remove-port=2222/tcp --permanent
 .firewall-cmd --reload
 .firewall-cmd --list-all

* To check the which port work on the service
 
 for example:
 .cockpit.socket

 .systemctl status cockpit.socket
 .systemctl enable cockpit.socket --now
 .systemctl status cockpit.socket

 * To check the server which port works on it
   .https://xxxxxxxx:xxxx