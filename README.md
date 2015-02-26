# Best terminal commands


## Server

### Reload hosts
````
dscacheutil -flushcache; sudo killall -HUP mDNSResponder
````
## SVN

### Remove .svn folders
````
find . -name ".svn" |xargs rm -rf
````

### Add new files
````
svn status | grep "^\?"  | awk '{print $2}' | xargs svn add
````
### View file differences
````
svn diff -r 'head' path/file
````
### View log for a specific revision
````
svn log -vr r46924
````
### Svn Delete all locally missing files (Mac Version)
````
svn st | grep ^! | awk '{print " --force "$2}' | xargs svn rm
````
### View pending update files
````
svn status -u
````



