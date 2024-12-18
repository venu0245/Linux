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
  
* use one time `ssh-keygen`
* one to another machine communicate without password-less 
* both machines have create .ssh folders
  ```
  cd .ssh
    id_rsa  id_rsa.pub  known_hosts
  ```
* connect one to one machine without passwordless we have `authorized_keys`

  ```
  cd .ssh
    authorized_keys  id_rsa  id_rsa.pub
  ```
* transfering data one to one machine with `rsync`
 
 ```
 rsync -avz ssh /test1 192.168.10.61:/test2
  a=>archive
  v=>verbose
  z=>zip
  rsync -avz ssh /test1 192.168.10.61:/test2 --dry-run
  rsync -avz ssh /test1 192.168.10.61:/test2 --delete
 ```