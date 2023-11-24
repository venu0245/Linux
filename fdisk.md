### HARD DISK PARTITIONS

* make a  hard disk  new partitions 'DOS'

* check how many partitions 
  ```
   fdisk -l
   ```

* make a new partition for extended after than logical create partition 

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
* make a file system for the new partition 

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




  
  
