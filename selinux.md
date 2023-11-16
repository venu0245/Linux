SELINUX
---------

getenforce

setenforce

sestatus

setenforce 1|0 
   1-->enforcing
   2-->permissive

 to temporvary set for enforcing and premissive mods 
    setenforce enforcing |permissive

 to permanent set for
    vim /etc/selinux/config

##create a dir. /app

 To access the publice content for dir. and files
   for /dir
   chcon -t publice_content_t /app

  for /dir in files  
   chcon -Rt publice_content_t /app

  for restore normal content 

    restorecon -R /app

To access the http,ftp,servers and applications for /dir

 cat /etc/selinux/targated/contexts/files/file_contexts.local

 ==>semanage fcontexts -a -t shamba_share_t /app

 after applying the access to the /dir

 ==> restorecon -R /app

 to access the httpd for dir in that having the files "/app(/.*)?"

  semanage fcontexts -a -t httpd_sys_content_t "/app(/.*)?"

 to access the HTTPD for empty dir /app

semanage fcontext -a -t httpd_content_t /app


BOOLEANS: (0,1)
------------
 semanage boolean -l|grep -i mysql
 
  for temporary to connect the on & off 

 getsebool -a |grep -i mysql ,ftp,httpd

 setsebool mysql_connect_any 1 (on), 0 (off)
  
  for permanent to connect the on & off
  setsebool -P mysql_connect_any on & off


