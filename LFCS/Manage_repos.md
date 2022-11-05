
we can find all of the installed repos in : /etc/yum.repos.d/

## To check installed repos/packages 
<pre>
sudo dnf repolist -v # this points us the repo's online address 
sudo dnf repolist --all 

# to enable/disable repos 
sudo dnf config-manager --enable 'package_name'
sudo dnf config-manager --disable 'package_name' 

# to add an external repo 
sudo dnf config-manager --add-repo https://---

# to remove a repo 
sudo rm /etc/yum.repos.d/---.repo 

</pre>

## Using dnf
<pre>
sudo dnf remove 'package_name' 

# to identify file origin
sudo dnf provides /etc/anacrontab 
sudo dnf repoquery --list nginx | grep 'search_string' 

</pre>
