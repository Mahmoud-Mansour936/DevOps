# Installing and downloading

## Installing

```bash
apt install [package] --> to install package
-y --> to agree if there is y/n question # for automation 
apt search [package] --> to search the package
apt update [package] -> to update specific package 
apt upgrade --> to update all packages on system # too important to have the last updates
apt remove --> remove package # but if there are conf files of it ,  it won't be removed
apt purge --> remove all things related to this package 

rpm -i --> install package 
... -e --> uninstall ...
... -q --> query package : we write the packages after it and we can see what is not 
unistalled 

yum install --> install application with its software and programms but sometimes 
i need something doesn't exist or it doesn't install the latest version : we can write
the specific version after the package name 

yum repolist --> to see repositries in system 

ls  /etc/yum.repos.d/ -> to see the list of repositry

 yum remove --> to uninstall package 

 yum list --> to see the versions

```

## Downloading

```bash
curl url -> Shows the raw HTML or content of the page
-o --> to download file 
-I --> Check if a URL is reachable

wget ...... .. filename --> download file into file 

# check os version #
ls or cat   /etc/*release*
```