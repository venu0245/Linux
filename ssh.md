## ADMIN REMOTE SYSTEM 

* ssh--> secure shell
* to connect one machine to another machine by using <ssh>

### for password authentication 

* To connect one machine to another machine
 .<ssh 192.168.10.61>

* To transfer the data in files/directories from to another machine
  for file
 .scp <_name of the file_> 192.168.10.61:/<_name of the folder_>  (for another machine)

* for directory 
 .scp -r <name of the directory>192.168.10.61:/<_name of the folder_>  (for another machine)

### No password authentication 
* To create a public and private keys we execute command as in (machine 192.168.10.60)
 .ssh-keygen (3time enter)
 .cd .ssh/
 .ls
  <id_rsa  id_rsa.pub  known_hosts>

* we can check the .ssh folder for another machine (192.168.10.61)
* if now ? as we can create .ssh folder 
 .ssh 192.168.10.61
 .ls -a
 .cd .ssh/
 .ls
   <known_hosts>

* from 60  to 61 machine to share the public key
 .from 60 machine we execute a command as
 .ssh-copy-id -i id_rsa.pub 192.168.10.61

 * from 61 we can check public key (authorized key) are not
  .ls
  .<authorized_keys  known_hosts>

 * now come to the 60 machine we can run as any command for example:
  .ssh 192.168.10.61 uptime
  .ssh 192.168.10.61 date
  .ssh 192.168.10.61 tail /etc/passwd

 * try to 61 machine we can run a command as 
  .ssh 192.168.10.60 tail /etc/passwd
    root@192.168.10.60's password:
 * it showing passwd (not shared any key from 192.168.10.60 to 192.168.10.61)   

 * to connect multi user also 
  .ssh -l 192.168.10.61 <username>


### same to create 61 machine to 60 machine ssh-keygen
 .<ssh-keygen> (enter 3times)

* 61 machine to generates the authorized keys (public keys)
 .authorized_keys  id_rsa  id_rsa.pub  known_hosts

* now we can test the machine 60 with asking password
```
 .ssh 192.168.10.60
 .ssh 192.168.10.60 uptime
 .ssh 192.168.10.60 tail /etc/passwd
 .ssh 192.168.10.60 useradd <username>
```
### rsyn (remote syncorization)
* same thing and parellel on both the machines
* to tranfer the data 60-->61,61-->60 by ssh
* create a directory mkdir /apt1 in 60 
* create a directory mkdir /app in 61
 
* rsync -avz -e ssh /app 192.168.10.61:/opt1

 .a-->archieve
 .v-->verbos
 .z-->gzip
 .ssh-->trust relation

* to add a data in dir/file to transfer 
 .rsync -avz -e ssh  /app 192.168.10.61:/opt1 --dry-run
  dry-run is preview command

### cronjob 
* sheduled the task in cronjob for specific time

. crontab -l
. crontab -e

  05 18 13 10 * rsync -avz -e ssh /opt1 192.168.10.61:/web 
.wq!
* now check the time to generate the task 
.date
  /opt1 on 60 & /web on 61





 




 