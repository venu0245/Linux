# MAIL SERVER

### port.no:25 smtp
### packages:postfix and dovecot
### configuration file:/etc/postfix/main.cf
###                   :/etc/dovecot/dovecot.conf 
### daemon:postfix,dovecot


#### from server side (60)

* we can install postfix and dovecot* packages
```
dnf install postfix* dovecot* -y
```
  
* vim /etc/postfix/main.cf
  se nu
  ```
    94=
    102=
    118=
    132=
    135=
    182=
    183=
    283=
    336=
     
  ```
  ![preview](images/mail1.PNG)
  ![preview](images/mail2.PNG)
  ![preview](images/mail3.PNG)
  ![preview](images/mail4.PNG)
  ![preview](images/mail5.PNG)
  ![preview](images/mail6.PNG)

* vim /etc/dovecot/dovecot.conf
* line 24 uncomment & delete submission woard
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

  ``` 
  .cd /var/named
  .vim /var/named/my.flz  
  ``` 
   ![preview](images/mail12.PNG)
   ![preview](images/mail15.PNG)

   ```
   .dnf install mail* -y
   ```
   ![preview](images/mail16.PNG)
 

 ### from another machine 61
 #### lab-setup

* dnf install postfix mailx -y
 ```
 .vim /etc/postfix/main.cf
 
 (132,336) uncomment the line
 (135)# comment the the line
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
  




