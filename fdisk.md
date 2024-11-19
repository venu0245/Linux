### HARD DISK PARTITIONS

#### DOC/GPT

* how many partitons are update in kernel 
  ```
  cat /proc/partitions
  ```

* how to update the kernel

  ```
  partprobe
  ```

* create a new partitions 

* check how many partitions 
  ```
   fdisk -l
   ```

* make a new partition first create extended partition  and after than create logical partitions 

  ```
  fdisk /dev/sda
  ```
  ![preview](images/disk1.PNG)  
  ![preview](images/disk2.PNG)

* create a new logical partition 

  ```
  fdisk /dev/sda
  ```
  ![preview](images/disk3.PNG)
  ```
  lsblk -f -->shows what type of partitio and which type of file system attached
  blkid
  df -h
  df -hT
  ```
* formate the file system to the partition ext4/xfs

  ![preview](images/disk4.PNG)

* mount with the directory with partition & create a new directory with names as /test

  ```
  mount /dev/sda5 /test
  ```
  ![preview](images/disk5.PNG)
  ![preview](images/disk6.PNG) 

* make a permanent mounting for a new partition fstab

  ```
  vim /etc/fstab
  ```
  ![preview](images/disk7.PNG)
  ![preview](images/disk8.PNG)
* after permanent mounting  

  ```
  UUID-->device name
  /dir-->mount point
  ext4/xfs-->file system
  defaults-->mount option
  0 0-->dumping,check squence (fsck)
  ```
* after permanent mounting we execute  
  ```
  mount -a
  ```
  ![preview](images/disk9.PNG)

* umount & remount
  ```
  umount /test
  mount /dev/sda5
  ```

* if someone user login into mount directory,
* as a root user when we umount the directory,mount directory will not be umount
* we can be check it out who inside the directory

  ![preview](images/disk10.PNG)

* check the who is inside the directory 

 ```
 lsof /test
 ```
 ![preview](images/disk12.PNG)

* send the message to user who login into directory `ctrl+d` is sending message to the user

 ```
 write venu
 ctrl+d
 ```
 ![preview](images/disk11.PNG)

* forcefully to remove the user from directory
 ```
 fuser -ck /<directory_name>
 ```
* permanent mounting in fstab
  vim /etc/fstab
  ```
 
  UUID      mount<directory>     filesystem <ext4/xs>  defaults(mount option)  0 0(dumping,check sequence fsck)

  ```
* after permanent mounting,we execute a command as 
  ```
  mount -a
  ```
* troubleshoot in `fstab` when enter the wrong data 
* when we poweron the machine system will be booting then
* skip the booting 
  ```
  CONTROL-D
  ```
## with parted command 

*  parted -l 
   ![preview](images/disk13.PNG)

* create a new partition with parted command

*  ```
   parted /dev/sda
   ```   
  ![preview](images/disk14.PNG)
  ![preview](images/disk15.PNG)

* to remove the partition 
  ![preview](images/disk16.PNG)

* formating ,mounting same as above images (images/disk4)

####  GPT

  starting size is previews disk size and end  sizes is it's own  size as per GB/MB
*  ![preview](images/disk17.PNG)
   ![preview](images/disk18.PNG)



   
  






  
  
