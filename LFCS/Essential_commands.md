# Loginng in to GUI / console 

to remotely connect to GUI:
VNC : used to connect to a remote GUI ( vncviewer ) 
RDP : used to connect to a remote GUI ( windows desktop ) 

to remotely connect to a console ( text-mode login  ) 
ssh ( strong encryption )
telnet ( not secure ) 

# hard links & soft links:

## Hard links 
<pre> $ stat <file> </pre> 
=> this command shows us the inode number ( used to keep track of metadata : permissions, when the data was last modified … )
=> it also shows ‘links’ nb ( for exp if a file has 3 links, then this param value is 3 ) 

File ⇒  inode  ⇒  blocks of data     | ⇒ : points  |   

use case of hard links:
suppose we have a directory that has 40GB of data, this directory is initially under /home/aaron/Pictures/ .. we want to move it to /home/jane/Pictures. 
If we simply copy it , we would have 40GB twice which is a lot 
so instead, we can just create a hard link of the directory :
<pre> $ ln  /home/aaro/Pictures/<filename>   /home/jane/Pictures/<filename> </pre>  
by creating a hard link, the 2 directories point to the same inode nb and the ‘link’ directory has 0 size ( it just points to the original directory ) 

If we delete the original file, the hard link remains intact 
we can only hard link FILES , also hard links to files must be on the same filesystem 

## Soft links 
they’re mainly used for creating shortcuts 
<pre> 
$ ln -s </pre>

# SUID, SGID and sticky bit 

when sticky is set on the file, it means the file will be executed as the user id owner of the file and not by the user that wants to execute it ( this is good for security reasons )

to enable SUID permission to a file ( user ) 
<pre>
$ chmod 4664 file     // here, SUID is set for the user owner 
</pre>
=> you’ll see S in the user file permission 

to enable SGID to a file ( gp  )
<pre>
$ chmod 2664 file 
</pre>
=> S in the gp permission 

to enable sticky bit perm on a directory  ( sticky bit is ‘t’ in the permissions ) 
<pre>
$ chmod 1664 
</pre>
to find SUID files in the current directory: 
<pre>
$ find . -perm /4000
</pre>
# How to search for files in Linux?

Syntax:
<pre>
$ find <path>  -<parameter>  <argument> 
</pre>
examples of parameters:
* name 
<pre>
$ find -name “f*” ( all files starting with ‘f’ letter are listed ) 
</pre>
* iname   
* type 
<pre>
$ find /var -type f      ( find stuff of type file )  
</pre>
* size   ( 512k, -512k ( less than ) ) 
 there’s also : c ( bytes ); M ( megabytes ); G (gigabytes ) ) 
* perm
<pre>
$ find -perm 664
$ find -perm -664   ( show files that have these permissions or more : 667 for exp )
$ find -perm /664   ( shows files that have any of the permissions, 600, 764 .. )  
</pre>
* mmin ( modified minute ) 
* mtim ( modified time - 24-hr period ) 
we specify nb of hrs as argument 
* exec 
<pre>
$ find -name “f*” -size 512k       ( AND operator ) 
$ find -name “f*” -o -size 512k   ( -o : OR operator ) 
$ find -not -name “f*” 
</pre>
we can specify 2 params:
<pre> 
$ find -name “f*” -size 512k       ( AND operator ) 
$ find -name “f*” -o -size 512k   ( -o : OR operator ) 
$ find -not -name “f*” 

$ find /user/share/ -name ‘*.jpg’ 
$ find /lib64/ -size +10M
$ find /dev/ -mmin -1  ( find files modified in the last 1 minute ) 
</pre>

# Manipulate content of file:

if u wanna see only last 20 lines of the file:
<pre> 
$ tail -n 20 /<path to file>
</pre>
if u wanna see first 20 lines of file:
<pre> 
$ head -n 20 /<path to file> 
</pre>
search and replace all occurrences of ‘canda’ with ‘canada’ :
<pre> 
$ sed ‘s/canda/canada/g’   file.txt 

$ sed -i ‘s/canda/canada/g’ -i file.txt   ( change directly in place - in the file - ) 
</pre>

extract the first column of the file 
<pre> 
$ cut -d ‘  ‘  -f  1 file.txt    (-d : delimiter   |    -f  : field   <column nb> ) 
</pre>
 to see differences between files 
<pre> 
$ diff -c file1 file2 
$ sdiff file1 file2   ( side by side comparaison ) 
</pre>




