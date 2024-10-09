## NFS (NETWORK FILE SYSYEM)
* port:2049
* NFS:network file system
* rpm -q nfs-utils
* /etc/exports

### From server side (192.168.10.60)
* we can setup 

* create a directory name as </nfs>
 ```
 .mkdir /nfs
 .cd /nfs
 .ls -ld /nfs
 .chmod 777 /nfs
 ```
 
*  connect any machine form server to any machine
* we can configure the file 

 ```
  vim /etc/exports
  /nfs 192.168.10.0/24 (rw,sync)
  wq!
  exportsfs -rv
 ``` 
  

* check the nsf-server.service enable/disable

 ```
  .systemctl status nfs-server.service
  .systemctl enable --now nfs-server.service
  .systemctl status nfs-server.service
 ```

* add services {nfs,mountd rpc-bind}
  ```
   .firewall-cmd --list-all
   .firewall-cmd --add-service=nfs --permanent
   .firewall-cmd --add-service={mountd,rpc-bind} --permanent
   .firewall-cmd --reload
   .firewall-cmd --list-all
  ``` 

### From client side (192.168.10.61)

 to test the communication from client to server
  ```
  .showmount -e 192.168.10.60
      Export list for 192.168.10.60:
       /nfs (everyone)
  ```     

* we can setup 

* create a directory name as </nfscl

  ```
  .mkdir /nfsc
  .mount -t nfs 192.168.10.60:/nfs /nfscl
  .mount |tail -4
    192.168.10.60:/nfs on /nfsc type nfs4
  .cd /nfscl
  .ls
  .umount -f /nfscl
  ```

 #### for permanent mounting 
  .vim /etc/fstab
  ```
    192.168.10.60:/nfs   /nfscl   nfs    defaults 0 0
  .wq!
  ```
 .mount -a
 .mount |tail -4
 
#### for auto mounting
* we can install a package `autofs`

 ```
 .dnf install autofs -y
 .vim /etc/auto.master
   /- /etc/auto.nfs --timeout=10
 .wq!
 
 .vim /etc/auto.nfs
  /nfscl -rw  192.168.10.60:/nfs 
 .wq!
 ```
 ```
 .systemctl status autofs.service
 .systemctl enable --now autofs.service
 .systemctl status autofs.service
 ```

* check the mount point 
  .mount |tail -4
  
* we can inside the directory
  .cd /nfscl
  .ls

* we can outside the directory
  .cd /nfscl

* observe the mount point
 .mount |tail -4

* when outside the directory still wait for 10 sec from(vim /etc/auto.master)



### limitation :
* only it can be connected into linux to linux & linux to unix


## SAMBA SERVER

## for linux machine 192.168.10.61
## port no: 449

* samab server is connect to linux to windows & linux to linux

### Lab setup
 1.install samba application
  
* create a directory name as /samba
 ```
  dnf install samba* -y
   .mkdir /samba
   .chmod 777 /samba
   .ls -l /samba
   .ls -ldZ /samba
    root unconfined_u:object_r:default_t
   ``` 

*  Set SELinux labels only on files and directories
 ```
 .chcon -t samba_share_t /samba
 .ls -ldZ /samba
   root root unconfined_u:object_r:samba_share_t:s0 
 ``` 

* to remove samba_share_access for directory
 ```
 .ls -lZd /samba
 .restorecon --help
 .restorecon -R /samba
   root root unconfined_u:object_r:default_t:s0
 ```

* add a user for samba server only
 ```
 .adduser samb

* to set password for samba user <smb>    
 .smbpasswd -a <smb> 8- characters (redhat@123)

  to remove the samba passwd 
 .smpasswd -x <smb>
 
 .pdbedit -l

 .pdbedit --help
 .pdbedit -u samb
 ```

* configuration file for samba
 ```
 .cat /etc/samba/smb.conf.example

   [public]
;       comment = Public Stuff
;       path = /home/samba
;       public = yes
;       writable = no
;       printable = no
;       write list = +staff
 ```

* we can modified the file and uncomment the line then after modify
 ```
  [GitShare]
       comment = my private 
       path = /samba
       public = no
       valid users = samb
       writable = yes
       hosts allow = 192.168.10.

  .wq!
  ``` 
  ```
* to check the file is working or not
  .testparm & enter
  ```
 * linux to windows 
 ```
* login as windows terminal as
    <PC> right click 
       networkdrives
       \\ip\share-name
  .username smb
  .password samba123
  .disconnect
  ```
  ![preview](images/smb2.PNG)
  ![preview](images/smb3.PNG)
  ![peview](images/smb4.PNG)
* windows to linux  
  ![preview](images/smb5.PNG)
* linux to windows
  ![preview](images/smb6.PNG)  
* linux to linux
  ![preview](images/smb7.PNG)  

 ### from client side (192.168.10.61) 
* we can install a package 

 ```
  .dnf install samba-client cifs-utils -y
  .dnf install samba-client-libs-4.15.5-5.el8.i686 -y
 ```
* create a directory with name as
 ```
   mkdir /sambacl
   cd /sambacl
   mount -t cifs //192.168.10.60/GitShare /samba1 -o user=smb  
 ```
 ![preview](images/smb1.PNG)
        

 



 







