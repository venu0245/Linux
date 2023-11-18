### BACKUP & RESTORE


* To find the folder were we want to take backup & name to create a bakup folder
```
 .du -h /etc
``` 
 ![preview](images/backup1.PNG)
 

* To take the backup for the folder or file we can
 ```
 .tar -cvf /backup/read.md /etc
 ```
 ![preview](images/back23.PNG)

 ```  
   .backup => folder/directory
   .etc.tar=> name of the backup
   .etc => stored data
   .cd /backup
 ```  
 ```
 . inside the directory we can take the backup
 ```
 ![preview](images/back24.PNG)

 .compressing the data by using 'gzip,unzip command 
 ```
 .du -h etc.tar.gz
 ```
 ![preview](images/back25.PNG) 
 ```
 .gzip etc.tar
 ```
 ![preview](images/back26.PNG)
 ![preview](images/back27.PNG)

 ```
 gunzip extra the data
 ```
 ![preview](images/back28.PNG)

```
. extrating the data and backup
```
 ![preview](images/back28.PNG)

```
. take backup together and gzip
```
. tar -zcvf /backup/etc.tgz /etc/ |tail -5
 
![preview](images/back29.PNG)

```
.extra the data for each create a file
```
![preview](images/back30.PNG)



 
 
     


    
 

