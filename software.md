### SOFTWARE MANAGEMENT:

#### RPM & YUM(DNF): 

* RPM :Redhat package management

*  connect Rhel-dvd in virtual box in that optical drive
 ![preview](images/sftw0.PNG)

* mount the dvd path hidden folder or manual folder 
 
*  ls /
*  mount /dev/sr0 /media (/media is default hidden folder)
  
* change the directory into /media folder

* cd /media
* ls
  AppStream & BaseOS 
* cd /media/BaseOS/Packages/
* ls

* install any package we change the directories or we can directly installed

* install,update &remove packages:

* cd /media/BaseOS/Packages/
* check rpm packages installed or not 
* we can changes the directories or we can installed directly
  
* rpm -qa <package_name>
* rpm -qi  <package_name>
* rpm -ivh zsh-5.5.1-9.el8.x86_64.rpm  (or) 
* rpm -ivh /media/BaseOS/Packages/zsh-5.5.1-9.el8.x86_64.rpm 
* rpm -Uvh zsh-5.5.1-9.el8.x86_64.rpm
* rpm -evh zsh-5.5.1-9.el8.x86_64.rpm
 
* verfiy the install package
  
* rpm -q zsh
  zsh-5.5.1-9.el8.x86_64
       
* query the information the package
  
* rpm -qip zsh
  
#### Command corrupted: (Troubleshooting)

* if any command not working or corrcupted 
  
  for example:
* date and mount commands

* which date
  /usr/bin/date
* which mount
  /usr/bin/mount
   
  ![peview](images/sftw1.PNG)

* find the path of the corrcupted command
     
* cd /media/BaseOs/Packages
* rpm -qf /usr/bin/mount   
* rpm -ivh coreutils-8.30-12.el8.x86_64.rpm --force
  
  ![peview](images/sftw2.PNG)

* check how many configuration files
  
* rpm -qa |wc -l (configuration files list)
* rpm -qlc sudo (query list configuration)
* rpm -qld sudo (query list documentation)
  
#### YUM OR DNF:(Yellow dog updater)

#### Lab set-up on server side:

* install the package vsftpd by using rpm 
* check the status of vsftpd.service

* cd /media/AppStream/packages/
* rpm -ivh /media/AppStream/packages/vsftpd
* systemctl status vsftpd
* systemctl enable --now vsftpd.service
  
* copy the whole mount directory into one directory 
    
* cp -rvf /media /var/ftp/pub/<name_folder>
    
* vim /etc/vsftpd/vsftpd.conf
  ```
  # Allow anonymous FTP? (Beware - allowed by default if you comment this out).
    anonymous_enable=YES
  ```  
* check and the firewall

* fiewall-cmd --list-all
* firewall-cmd --add-service=ftp --permanent
* firwall-cmd --reload
 
* configure the repository file

* vim /etc/yum.repos.d/my.repo
  ```
  [AppStream]
  name=Local_AppStream_repo
  baseurl=file:///var/ftp/pub/venu/AppStream
  gpgcheck=1
  enabled=1
  gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

  [BaseOS]
  name=Local_BaseOS_repo
  baseurl=file:///var/ftp/pub/venu/BaseOS
  gpgcheck=1
  enabled=1
  gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

  ``` 
* check weather file fuctioning or not
  
* dnf clean all
* dnf provides zsh/ftp/httpd
   
#### From client side:
* configure the repository file

* vim /etc/yum.repos.d/cl.repo
 ```
 [AppStream]
 name=FTP_AppStream_repo
 baseurl=ftp://192.168.10.60/pub/venu/AppStream
 gpgcheck=1
 enabled=1
 gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

 [BaseOS]
 name=FTP_BaseOS_repo
 baseurl=ftp://192.168.10.60/pub/venu/BaseOS
 gpgcheck=1
 enabled=1
 gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
 ```
* dnf clean all
* dnf provides zsh

* test ftp working or not in command prompt
* ftp 192.168.10.60
   ftp
   ls

* dnf repolist
* dnf list
* dnf list installed
* dnf install zsh -y (BaseOS)
* dnf intall httpd -y (AppStream)
* dnf update httpd/zsh
* dnf info httpd/zsh
* dnf remove httpd/zsh
* dnf grouplist
  
 