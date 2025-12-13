### Patching activity:
 ```
 * thersold (cpu) value is greaterthan 85% disk value get notification alterts in servicenow/itil tool (both monitoring tools are same)
 * inform the application team take backup for y our's data 
 * login into terminal and after than check the kernal version and kernal architecture
connect to redhat developer website with login username and pasword
 Self-introduction:

 * Hi,I have 4+ years of experience as Redhat Aws+Linux administartor.
 
 * MY Day-to-Day activities starts with Monitoring servers, Handling Incidents, Serivce Requests, Planning and Scheduling Change Requets.
 
 * Here in our project, we are performing redhat linux patching for every month.
  
 * We are using As know as Monitoring and Ticket tool.

 * Linux Patches, are categorised into High, Medium and Low levels.
  
 * High Findings need to remediate in 30days, Medium in 60 days and Low in 90 days.
  
 * Here there is a agent called Qualys deployed in all servers, which tracks the Vulnerabilites
  
 * We are supporing for 500+ servers Invetory, all are Virtual servers.
  
 * We are a team of 9 members working on shifts and supporting 24/7
  
 * In Addtion to Redhat linux patching we perform OS upgrades
  
 * We are perfrming patching by registering the servers with redhat linux satellite servers with redhat subscription
  ```
#### Monitoring commands:*
* cpu=>sar -u 1 2
* memory=>vmstat 1 2
* i/o=>iostat 1 2
 iostat -d sda
 iostat -d sda3 1 3
* Network=>netstat -ntulp
 nestat -i 1 2  
 
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

