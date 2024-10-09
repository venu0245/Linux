  ### Remote adminstration SSH    
* SSH: secure shell
 .one machine to another machine connect each other
 .for example:
 ```
  ssh 192.168.10.61
 .in another machine have a user we can possible for login 
  ssh -l v1 192.168.10.61
 .sharing files and directories for another machine
  scp -r app 192.168.10.61:web
  -r -->rescursively only for directory
 ```
* RSYNC:some time and same thing available
 ```
 rsync -avz <dir_name> <ip_addr>:<dir_name>
  .if we delete the files/directories we can run the
  rsync -avz <dir_name> <ip_addr>:<dir_name> --delete
 ```
 #### Password authentication:SSH-KEY
 * check weather we have .ssh folder is their not ,if not .ssh
   ```
   ssh 192.168.10.60/61 
    cd .ssh
    ls
    ssh-key-gen
   .to copy the public key to share the another machine
    ssh-copy-id-i  id_rsa.pub 192.168.10.60/61
   ```
