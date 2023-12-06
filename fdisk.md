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

* create a hard disk with new partitions 

* check how many partitions 
  ```
   fdisk -l
   ```

* make a new partition first create extended  and after than create logical partition 

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
  lsblk -f
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
  
  ```
  mount -a
  ```
  ![preview](images/disk9.PNG)

* umount & remount
  ```
  umount /test
  mount /dev/sda5
  ```

* if some user login into our directory,if we umount the directory as a root

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

* in fstab by mistake we enter wrong and save ,if we poweron the machine type `control-D login & fix the error

  ```
  control-D
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



   
  






  
  
