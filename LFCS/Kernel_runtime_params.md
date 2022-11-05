
## SELinux 

it's an access control ( it controls what objects on our host can communicate with other objects on the same host ) 

SELinux modes:
* enforcing : SELinux is actively permitting/preventing comm. based on the label of each object 
* permissive
* disabled : SELinux is disabled

To define SELinux mode, either:
* edit the file /etc/sysconfig/selinux 
* use one of these commands: $getenforce  or  $sestatus 

Labels and Policies:
* Policies: they're rules that tell SELinux what to do ( in /etc/sysconfig/selinux ,there's this var SELINUXTYPE that we can assign to it one of these 
values : targeted / minimum / MLS ) 
* Labels: the control what object can communicate with other objects in the host 

To see labels:
<pre>
ls -lZ /path_to_file 
ps axZ | grep 'process' 
</pre>

Type enforcement and managing labels 
* Managing labels 
<pre>
chcon -t httpd_syscontext_t   /var/www/html/index.html 

# go back to default label 
restorecon -vR /var/www/html 
</pre>

when we want to preserve security context, we add --preserve=context 
