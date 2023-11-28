## SWAP MANAGEMENT SPACE

* minimum  `RAM` size to create a swap in system `4 Gb`

* ```
  swapon (activate the partition)
  swapoff(de-activate partition) 
  mkswap (format)
  swap (file-system)
  free -h (checking sizes)
  82 (code-swap) 
  ```

* create a swap partition minimum `1GB`

   ```
   fdisk /dev/sda
     .n
     .t
     .l
     .82
     .w
   ```
  ![preview](images/swap0.PNG)
  ![preview](images/swap1.PNG) 
* make a file system for partition 
  ![preview](images/swap2.PNG)
* check the sizes of partition `swapon & swapoff` by using `free -h`
  ![preview](images/swap3.PNG)

* permanent mount `vim /etc/fstab`
  ![preview](images/swap4.PNG)       
* testing the fstab `mount -a`

* removing the swap partition `parted /dev/sda rm 6`

### create a swapfile

*  df -h /swapfile

* ```
  dd if=/dev/urandom of=/swapfile bs=1m count=1024
  
  dd-->dumped data
  if-->input for/dev/urandom
  of-->output for /dev/urandom
  bs-->block per secound
  count-->1024 (size of Gb)
  ```
  ![preview](images/swap5.PNG)

  ```
  chmod 600 /swapfile
  mkswapfile /swapfile
  swapon /swapfile
  df -h /swapfile
  ```
  ![preview](images/swap6.PNG)



