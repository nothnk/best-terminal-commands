# Developer commands

A list of commands i use everyday as developer

## Table of Contents

- [Server](#server)
- [Svn](#svn)
- [Utils](#utils-macosx)
- [Symfony2](#symfony2)

- - -

## Server *(4)*

- Reload hosts
````
dscacheutil -flushcache; sudo killall -HUP mDNSResponder
````
- Check free disk space
````
df -h
````
- Reports the sizes of directory trees
````
du -h
````
- Change permissions of a directory/file to a user
````
chown -R username:usergroup path_to_change
````

## SVN *(9)*

- Remove .svn folders
````
find . -name ".svn" |xargs rm -rf
````

- Add new files
````
svn status | grep "^\?"  | awk '{print $2}' | xargs svn add
````
- View file differences
````
svn diff -r 'head' path/file
````
- View log for a specific revision
````
svn log -vr r46924
````
- Svn Delete all locally missing files (Mac Version)
````
svn st | grep ^! | awk '{print " --force "$2}' | xargs svn rm
````
- View pending update files
````
svn status -u
````
- Ignore files (in file folder)
````
svn propset svn:ignore file-to-ignore .
````
- view ignored files in the current directory
````
svn propget svn:ignore
````
- svn merge repo with an entire branch
````
svn merge svn://XX.XX.XX.XX/repo/branch
````

- svn merge only one file on a branch 
````
svn merge svn://XX.XX.XX.XX/repo/path/to/file local/path/to/file
````

## Utils (macosX) *(3)*

- Create formatted HFS Volume
````
hdiutil create -size 1000m -fs "Case-sensitive HFS+" -volname NameVolume NameFile.dmg
````
- Reset finder
````
rm ~/Library/Preferences/com.apple.finder.plist&&killall Finder
````
- Show folders/list size and showing MB/KB
````
ls -lahS
````

## Symfony2 *(4)*

- Generating a New Form Type Class Based on a Doctrine Entity
````
php app/console generate:doctrine:form AdminBundle:Contact
````
- Generate easy CRUD for an entity
````
php app/console generate:doctrine:crud --entity=AdminBundle:EntityName --route-prefix=entity_name --with-write --format=yml --no-interaction
````
- Show the pending changes to the database
````
php app/console doctrine:schema:update --dump-sql
````
- Write the pending changes to the database
````
php app/console doctrine:schema:update --force
````
## Drupal *(2)*

- Update drupal (https://fuerstnet.de/en/drupal-upgrade-easier)
````
patch -p1 < PATCHFILE
````
- Remove cache
````
drush cc all
````
## Git *(1)*

- Removing multiple files from a Git repo that have already been deleted from disk
````
git rm $(git ls-files --deleted)  
````
- Git commit direct
````
git add . ; git commit -m "Message" ; git push origin master 
````



