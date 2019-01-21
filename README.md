# Developer commands

A list of commands i use everyday as developer

## Table of Contents

- [Server](#server-10)
- [Svn](#svn-10)
- [Utils](#utils-macosx-5)
- [Symfony2](#symfony2-4)
- [Drupal](#drupal-2)
- [GIT](#git-3)
- [NPM](#npm-2)
- [Convert files](#convert-files-3)
- - -

## Server *(10)*

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
- Create link symbolic
````
ln -s origin_folder_or_file name_link
````
- Create tar.gz
````
tar -czvf name_file.tar.gz file_or_folder_to_compress
````
- Create tar.gz with date
````
tar -czvf "backup-$(date +%y-%m-%d--%H-%M-%S).tar.gz" file_or_folder_to_compress
````
- Extract tar.gz 
````
tar -xzvf name_file.tar.gz
````
- Create zip folder recursive
````
zip -r  "backup-$(date +%Y-%m-%d--%H-%M-%S).zip" file_or_folder_to_compress
````

- Restore backup mysqldatabase
````
mysql -u root -ppassworduser databasename < backup-file.sql
````
For MAMP
````
/Applications/MAMP/Library/bin/mysql -u root -ppassworduser databasename < backup-file.sql
````

## SVN *(10)*

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
- svn commit
````
svn ci -m "Message"
````

## Utils (macosX) *(5)*

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
- List of commands you use most often
````
history | awk '{print $2}' | sort | uniq -c | sort -rn | head
````

- Mount iso
````
hdiutil mount path/name-file.iso
````

- Find files in a path
```
find src/ui -name "index.js"
```

- Find and remove files in a path
```
find src/ui -name "index.js"  -exec rm -rf {} \;
```

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
## Git *(3)*

- Removing multiple files from a Git repo that have already been deleted from disk
````
git rm $(git ls-files --deleted)  
````
- Git commit direct
````
git add . ; git commit -m "Message" ; git push origin master 
````
- Git update
````
git pull origin master
````

## NPM *(2)*

- Listing globally installed NPM packages and version
```
npm list -g --depth=0
```

- Search if a package is installed locally

```
npm ls -g | grep -E "babelcli|crossenv"
```

## Convert files *(2)*
- Requirements: Install ffmpeg
```
1. xcode-select --install ([If you don`t have install xcode developer tools](https://apple.stackexchange.com/questions/254380/macos-mojave-invalid-active-developer-path)
2. brew install ffmpeg
```

## Convert mov
- Convert & scale mov to mp4 [convert-videos-mp4-format-using-ffmpeg](http://www.bugcodemaster.com/article/convert-videos-mp4-format-using-ffmpeg)
```
ffmpeg -i file.mov -vf scale=1280:720 -c:v libx264 -preset fast -c:a aac file.mp4 -hide_banner
```

## Sample function for ZSH

```
# ConvertVideo
convertVideo(){
  ffmpeg -i $1.mov -c:v libx264 -preset fast -c:a aac $1.mp4 -hide_banner
}
```

- Only Convert mov to mp4

```
ffmpeg -i sample..mov -c:v libx264 -preset fast -c:a aac sample.mp4 -hide_banner
```

- Convert m4a to mp3
```
ffmpeg file.mp3 -i file.m4a -codex:a libmp3lame -qscale:a 1
```

- Reduce mp4 file size 
```
ffmpeg -i input.mp4 -c:v libx264 -crf 24 -b:v 1M -c:a aac output.mp4
```
- Split AVi
```
ffmpeg -i video.avi -vcodec copy -acodec copy -ss 00:40:35 -t 0:3:00 out.avi
```

### Download files 
```
brew install wget
wget [--user=NAME --password='PASSWORD'] url/ftp/web
```

