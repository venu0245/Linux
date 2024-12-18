## SWAP MANAGEMENT SPACE
 `SWAP-code (82)`

* minimum size of  `RAM` in the local system `4gb`
* minimum size to create swap partition is `1gb` 

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
     .n-new
     .t-change type
     .l-listcodes
     .82-(code-linux swap)
     .w-saving
   ```
  ![preview](images/swap0.PNG)
  ![preview](images/swap1.PNG) 

* format the swap partition 
 ```
 mkswap /dev/sda6
 ```
  ![preview](images/swap2.PNG)
* check the sizes of partition `swapon & swapoff` by using `free -h`
  ![preview](images/swap3.PNG)

* permanent mounting in `vim /etc/fstab`
  ![preview](images/swap4.PNG)  

* after enter the details in fstab 
 ```
 swapon -a =>only swap
 mount -a =>only linux
 ```

* removing the swap partition `parted /dev/sda rm 6`

### creating a swapfile

*  df -h /swapfile

* ```
  dd if=/dev/urandom of=/swapfile bs=1M count=1024

  dd-->dumped data
  if-->input for/dev/urandom
  of-->output for /dev/urandom
  bs-->block per secound
  count-->1024 (size of Gb)
  ```
  ![preview](images/swap5.PNG)

  ```
  swapon /swapfile
  chmod 600 /swapfile
  mkswapfile /swapfile
  swapon /swapfile
  df -h /swapfile
  du -h /swapfile
  ```
  ![preview](images/swap6.PNG)



