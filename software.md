##### SOFTWARE MANAGEMENT ######

### RPM & YUM(DNF) ####

* RPM :Redhat package management

* 1. connect the dvd into virtual box
  2. mount /dev/sr0 /media (/media default hidden folder)

* change the directory to /media
 .cd /media
 .ls
   AppStream  BaseOS 
* check the packages in Base0s and AppStream  
 .cd /media/BaseOS/Packages/
 .ls
 
* to install any package we change the directories or we directly installed
 1. cd /media/BaseOS/Packages/ 
     rpm -ivh zsh-5.5.1-9.el8.x86_64.rpm  (or)

 2.  rpm -ivh /media/BaseOS/Packages/zsh-5.5.1-9.el8.x86_64.rpm  

* to update package 
 .rpm -Uvh zsh-5.5.1-9.el8.x86_64.rpm

* to uninstall the package or erase the package
 .rpm -evh zsh-5.5.1-9.el8.x86_64.rpm

* to verfiy the install package
 . rpm -q zsh
    zsh-5.5.1-9.el8.x86_64

* to query the information the package
 .rpm -qi zsh

## Command corrupted ## 

* check the path of the both commands (date & uptime)
 .<example>
* to find the path of the command: 
 .which date
  /usr/bin/date
 .which uptime
  /usr/bin/uptime

* to find the command path in <rpm -qf>
 .rpm -qf /usr/bin/uptime

* to installed the corrupted command package
 .rpm -ivh /media/BaseOS/Packages/<command package .rpm --force>

* to check the how many configuration files
 .rpm -qa |wc -l
 .rpm -qlc sudo 



 ### YUM INSTALLATION ###

* YUM:yellow dog updater
* AppStream packages (third party softwares)
* imstall vsftpd by rpm command
* rpm -ivh rpm -ivh /media/AppStream/Packages/vsftpd-3.0.3-35.el8.x86_64.rpm
* rpm -qi vsftpd 

* check the /var/ftp/pub 

* copy the whole media data into /var/ftp/pub

* cp -rvf /media /var/ftp/pub/<rhel8>(folder_name)
   AppStream  BaseOS are available

* check AppStream packages
 .cd /media/AppStream/Packages/
 .ls

* repository configuration file
  .vim /etc/yum.repos.d/my.repo
    [AppStream]
 name=Local_Appstream_repo
 baseurl=file:///var/ftp/pub/rhel8/media/AppStream
 enabled=1
 gpgcheck=1
 gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release


   [BaseOS]
 name=Local_BaseOS_repo
 baseurl=file:///var/ftp/pub/rhel8/media/BaseOS
 enabled=1
 gpgcheck=1
 gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
 .wq!

* to update the file 
 .yum/dnf clean all
 
* to check the packages for Appstream/BaseOS 
 .dnf provides zsh
 .dnf provides ftp

* to test the ftp is not or not in command prompt
  .ftp 192.168.10.60
   ftp
   ls

* confiuration file for vsftpd
 .vim /etc/vsftpd/vsftpd.conf   
   nonymous_enable=YES

* check the status of vsftpd
 .systemctl status vsftpd
 .systemctl enable vsftpd --now

* to add ftp in firewall
 .firewall-cmd --list-all
 .firewall-cmd --add-service=ftp --permanent
 .firewall-cmd --reload

### to configure the client server 192.168.10.60 ###
 .vim /etc/yum/repos.md/cl.repo
  [AppStream]
  name=FTP_AppStream_repo
  baseurl=ftp://192.168.10.60/pub/rhel8/AppStream
   enabled=1
   gpgcheck=1
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release


   [BaseOs]
   name=FTP_BaseOS_repo
   baseurl=ftp://192.168.10.60/pub/rhel8/BaseOS
   enabled=1
   gpgcheck=1
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release

   .wq!

 .dnf clean all
 .dnf provides zsh
 .dnf list installed
* to install packages 
 .dnf install zsh
* update package
 .dnf update zsh
* to remove package
 .dnf remove zsh

* to install group packages
 .dnf grouplist
 .dnf groupinfo 'development tools'
 .dnf groupinstall 'development tools'
 .dnf groupupdate 'development tools
 .dnf groupremove 'development tools   
 