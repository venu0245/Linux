* thersold value is 85% settled value value space and alterts in servicenow tool
* login into terminal and after than check for kernal version
connect to redhat developer website 
 ```
 cat /etc/redhat-release
 uname -r 
 subscription -manager register
 lsblk
 df -h
 df -Th
 yum history
 yum update
 ```
#### patching activity:
* discuss the application and scheduled plan for patch for patching time
* checking for kernel versoin
* check for disk spaces
* check for cpu utilization
* check for ram space
### for new version patch activity:
 ```
 cat /etc/redhat-release
 uname -r
 mode of kernel version
 rpm -qa |grep -i kernel
 ls /boot/vmlinux*
 grubby --default -kernel
 grubby set-default /boot/vmlinux
 reboot
 
 ```
