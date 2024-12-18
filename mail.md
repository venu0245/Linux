## MAIL SERVER

### port.no:25 smtp
### packages:postfix and dovecot
### configuration file:/etc/postfix/main.cf
###                   :/etc/dovecot/dovecot.conf 
### daemon:postfix,dovecot


#### lab set-up on server side (60)

*  install postfix and dovecot* packages
```
dnf install postfix* dovecot* -y
```
  
* vim /etc/postfix/main.cf
  se nu
  ```
    94=venu60.git.com-un-comment
    102=git-un-comment
    118=un-comment
    132=un-comment
    135=comment
    183=comment
    184=un-comment
    283=192.168.10.60 un-comment
    336=venu60.git.com
     
  ```
  ![preview](images/mail1.PNG)
  ![preview](images/mail2.PNG)
  ![preview](images/mail3.PNG)
  ![preview](images/mail4.PNG)
  ![preview](images/mail5.PNG)
  ![preview](images/mail6.PNG)

* vim /etc/dovecot/dovecot.conf
* line number 24-uncomment & delete submission word
   ![preview](images/mail7.PNG)
   ![preview](images/mail8.PNG)
  ```
  .systemctl status postfix dovcot
  .systemctl enable --now postfix dovecot 

  ```
  ![preview](images/mail9.PNG)
  ``` 
  .firewall-cmd --list-all
  .firewall-cmd --add-service=smtp --permanent
  .firewall-cmd --reload

  ```
  ![preview](images/mail10.PNG)
 
  .cd /var/named
  .vim /var/named/my.flz  
  
   ![preview](images/mail12.PNG)
   ```
   nslookup git.com
   ```
   ![preview](images/mail15.PNG)

  
  * dnf install mail* -y
   
 ### lab set-up machine 61
  

* dnf install postfix mailx -y
 
* vim /etc/postfix/main.cf
 ```
 132=un-comment
 135=comment
 336=venu60.git.com un-comment
 ``` 
 ![preview](images/mail17.PNG)

 ![preview](images/mail13.PNG)
  

* systemctle enable --now postfix

  ![preview](images/mail14.PNG)

 ```
 firewall-cmd --add=service=smtp --permanent
 firewall-cmd --reload  
 firewall-cmd --list-all
 ```
 ![preview](images/mail18.PNG)

 ```
 mail -s test root@venu60.git.com 
  after write the message 'ctrl+d' is sending mail
 ctrl+d
 ```
  ![preview](images/mail19.PNG)

* check the other machine60 we get mail message

 ![preview](images/mail20.PNG) 

* for relpying the another machine and quit after relpying

 ```
 .r
 ```
  ![preview](images/mail21.PNG)

 ```
  .mailq
  for checking previous mails details 
  .cd /var/spool/mail
 ```
 ![preview](images/mail22.PNG)
  




