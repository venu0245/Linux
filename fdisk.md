### HARD DISK PARTITIONS

#### DOC/GPT

* how many partitons are update in kernel 

* SCSI drive will be shown as /dev/sda
  ```
  cat /proc/partitions
  ```

*  update the kernel

  ```
  partprobe
  ```

* create a partitions with fdisk 

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
  lsblk -f = it's shows file-system and mount-point directory
  blkid = it's shows every uuid for partition /dev/sda (1,2,3...)
  df -h = 488M  780K  452M   1% /test
  df -hT = /dev/sda5      ext4      488M  780K  452M   1% /test
  ```
* format the file system to the partition ext4/xfs /dev/sda5

  ![preview](images/disk4.PNG)

* create a new directory
* mount the directory with partition number /dev/sda 

  ```
  mount /dev/sda5 /test
  ```
  ![preview](images/disk5.PNG)
* mount |tail -5  
  ![preview](images/disk6.PNG) 

* make a permanent mounting for a new partition in  `fstab`

  
*  vim /etc/fstab
  
  ![preview](images/disk7.PNG)
  ![preview](images/disk8.PNG)

  ```
  UUID-->device name
  /dir-->mount point
  ext4/xfs-->file system
  defaults-->mount option
  0 0-->dumping,check squence (fsck)
  ```
* mention uuid, dir, ext4/xfs, defaults 0 0
* after than we execute the command
  ```
  mount -a
  ```
  ![preview](images/disk9.PNG)

* umount & remount
  ```
  umount /test
  mount /dev/sda5
  ```

* someone user login into mount directory, it can be editing the mount directory in that files 
 
 ```
 lsof /test
 ```
  ![preview](images/disk10.PNG)

  ![preview](images/disk12.PNG)

* send the message to the user logout for the directory
 
 ```
 write venu
 ctrl+d
 ```
 ![preview](images/disk11.PNG)

* forcefully to remove the user from mount directory
 ```
 fuser -ck /<directory_name>
 ck-current activities
 ```
* permanent mounting in fstab
  vim /etc/fstab
  ```
  UUID      mount<directory>     filesystem <ext4/xs>  
  
  defaults(mount option)  0 0(dumping,check sequence fsck)

  ```
* after permanent mounting,we execute a command as 
  ```
  mount -a
  ```
* troubleshoot in `fstab` when enter the wrong data in fstab
* when we poweron the machine system will be booting then
* poweron
* skip the booting 
  ```
  CONTROL-D
  vim /etc/fstab
  ```
### parted command 

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



   
  






  
  
