# Best terminal commands


## Server
------------------------
### Reload hosts
````
dscacheutil -flushcache; sudo killall -HUP mDNSResponder
````
## SVN
------------------------
### Remove .svn folders
````
find . -name ".svn" |xargs rm -rf
````

### Add new files
````
svn status | grep "^\?"  | awk '{print $2}' | xargs svn add
````



