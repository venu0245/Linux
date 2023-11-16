#### NFS ####
* port:2049
* NFS:network file system
 .rpm -q nfs-utils
* server to client 
* client is connect to server download and upload data
* configuration file of nfs
* .vim /etc/exports


* setup for both machines 192.168.10.60 & 192.168.10.61

 .192.168.10.60 is server
 .192.168.10.61 is client

### from servser side (192.168.10.60)

* we create a directory of name </nfs>
 .mkdir /nfs
 .chmod 777 /nfs
 
*  connect any machine for server side we can configure 
 .vim /etc/exports
  /nfs 192.168.10.0/24 (rw,sync)
  .wq!

 * to execute the file 
  .exportsfs -rv

 * check the nsf-server.service enable/disable
  .systemctl status nfs-server.service
  .systemctl enable --now nfs-server.service
  .systemctl status nfs-server.service
  .exportfs -rv

 * add firewall for nfs
  .firewall-cmd --list-all
  .firewall-cmd --add-service=nfs --permanent
  .firewall-cmd --add-service={mountd,rpc-bind} --permanent
  .firewall-cmd --reload
  .firewall-cmd --list-all

* to test the communication for server to client
 .showmount -e 192.168.10.60
     Export list for 192.168.10.60:
      /nfs (everyone)

* #### from client side we can setup 192.168.10.61 

* create a directory name as <nfsc>
 .mkdir /nfsc
 .mount -t nfs 192.168.10.60:/nfs /nfscl
 .mount |tail -4
   192.168.10.60:/nfs on /nfsc type nfs4
 .cd /nfscl
 .ls
 .umount -f /nfscl

 * for permanent mounting 
  .vim /etc/fstab
    192.168.10.60:/nfs   /nfscl   nfs    defaults 0 0
  .wq!

 .mount -a
 .mount |tail -4
 

* for auto mounting we need install autofs
 .dnf install autofs -y
 .vim /etc/auto.master
   /- /etc/auto.nfs --timeout 10
 .wq!
 
 .vim /etc/auto.nfs
  /nfscl -rw  192.168.10.60:/nfs 
 .wq!

 .systemctl status autofs.service
 .systemctl enable --now autofs.service
 .systemctl status autofs.service

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



# limitation :
 .it can be connected to linux to linux & linux to unix


##### SAMBA Server ####

# for linux machine 192.168.10.61
# port no: 449

* samab server is connect to linux to windows & linux to linux

# steps
 1.install samba application
  .dnf install samba* -y
* create a directory for name of /samba
 .mkdir /samba
 .chmod 777 /samba
 .ls -l /samba
 .ls -ldZ /samba
    root unconfined_u:object_r:default_t

* to apply samba share access for directory
 .chcon -t samba_share_t /samba
 .ls -ldZ /samba
   root root unconfined_u:object_r:samba_share_t:s0 

* to remove samba_share_access for directory
 .ls -lZd /samba
 .restorecon --help
 .restorecon -R /samba
   root root unconfined_u:object_r:default_t:s0

* add a user for samba server only
 .adduser samb
 .pdbedit -l
 .pdbedit --help
 .pdbedit -u samb
  

* to set password for samba user <samb>    
 .smbpasswd -a <samb> 8- characters
* to remove the samba list 
 .smpasswd -x <samba user>

* configuration file for samba
 .cat /etc/samba/smb.conf.example

   [public]
;       comment = Public Stuff
;       path = /home/samba
;       public = yes
;       writable = no
;       printable = no
;       write list = +staff

* we can modified the file and uncomment the line after modified 
  [GitShare]
       comment = my private 
       path = /samba
       public = no
       valid users = samb
       writable = yes
       hosts allow = 192.168.10.

  .wq!

 * to check the file is working or not
  .testparm 
  .<enter> whatever changes can do in file 

* login as windows terminal as
    <PC> right click 
       networkdrives
       \\ip\share-name
  .username
  .password
  .disconnect


 ### linux machine to linux machine 
* we can install a package 

 . dnf install samba-client cifs-utils -y
  .dnf install samba-client-libs-4.15.5-5.el8.i686 -y

 .mkdir /samba1
 .cd /samba1
 .mount -t cifs //192.168.10.60/GitShare /samba1 -o user=smb  
        

 



 







