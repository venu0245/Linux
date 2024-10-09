## SWAP MANAGEMENT SPACE
 `SWAP (82)`

* minimum size of  `RAM` in the local system `4gb`
* minimum size to create swap partition should be `1gb` 

* ```
  swapon (activate the partition)
  swapoff(de-activate partition) 
  mkswap (partition name)
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
     .82(code-linux swap)
     .w
   ```
  ![preview](images/swap0.PNG)
  ![preview](images/swap1.PNG) 
* make a file system for partition 
  ![preview](images/swap2.PNG)
* check the sizes of partition `swapon & swapoff` by using `free -h`
  ![preview](images/swap3.PNG)

* permanent mounting in `vim /etc/fstab`
  ![preview](images/swap4.PNG)       
* after enter the details in fstab `mount -a`

* removing the swap partition `parted /dev/sda rm 6`

### create a swapfile

*  df -h /swapfile

* ```
  dd if=/dev/urandom of=/swapfile bs=1m count=1024
  m 
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



