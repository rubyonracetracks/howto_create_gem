# Chapter 1: Initial Commit
In this chapter, you will start a new Ruby gem and commit the source code to GitHub.

## Bundler
* Reset the Docker container based on one of the rbenv-general Docker images.
* In Docker, enter the following command:
```
bundler gem (name of gem)
```
* When prompted on the tests to use, select rspec.  (There are tutorials on the gem creation process, and most of them use RSpec.  Also, I prefer Minitest for Rails projects, so selecting RSpec for Ruby gems broadens my know-how.)
* When you are asked about whether you wish to license your code under the MIT license, enter "y" for yes.  (If there is any specific reason you do not wish to do so, then enter "n" for no.)
* When you are prompted on whether to include a code of conduct, enter "y" for yes.
* Use the "cd" command in Docker to enter the root directory of your app.

## credentials.sh

* Add the file credentials.sh to the root directory of your gem:
```
#!/bin/bash

# Output:
# First argument if it is not blank
# Second argument if first argument is blank
anti_blank () {
  if [ -z "$1" ]; then
    echo "$2"
  else
    echo "$1"
  fi
}

# Setting Git email if necessary
GIT_EMAIL="$(git config user.email)"
if [ -z "$GIT_EMAIL" ]; then
  EMAIL_DEF='you@example.com'
  echo
  echo "Default email address: ${EMAIL_DEF}"
  echo
  echo 'Enter your Git email address:'
  read EMAIL_SEL
  EMAIL=$(anti_blank $EMAIL_SEL $EMAIL_DEF)
  echo

  echo
  echo '------------------------------'
  echo "git config --global user.email"
  echo "$EMAIL"
  git config --global user.email "$EMAIL"
fi

# Setting Git name if necessary
GIT_NAME="$(git config user.name)"
if [ -z "$GIT_NAME" ]; then
  NAME_DEF='Your Name'
  echo
  echo "Default name: ${NAME_DEF}"
  echo
  echo 'Enter your Git name:'
  read NAME_SEL

  # NOTE: The double quotes are needed to avoid truncating the string
  # at the space.
  NAME=$(anti_blank "$NAME_SEL" "$NAME_DEF")

  echo
  echo '-----------------------------'
  echo "git config --global user.name"
  echo "$NAME"
  git config --global user.name "$NAME"
  echo
fi
```
* Enter the command "sh credentials.sh".  If you haven't already done so, you will be prompted to enter your Git credentials.  This allows you to git commit.
* Run the credentials.sh script every time you reset your Docker container, because your credentials get erased.

## .gitignore
* Add the following lines to the beginning of the .gitignore file:
```
########################
# BEGIN:initial contents
########################
```
* Add the following lines to the end of the .gitignore file:
```
#######################
# END: initial contents
#######################

################################
# BEGIN: Windows files to ignore
################################
# FROM https://github.com/github/gitignore/blob/master/Global/Windows.gitignore

# Windows image file caches
Thumbs.db
ehthumbs.db

# Folder config file
Desktop.ini

# Recycle Bin used on file shares
$RECYCLE.BIN/

# Windows Installer files
*.cab
*.msi
*.msm
*.msp

# Windows shortcuts
*.lnk
##############################
# END: Windows files to ignore
##############################

#############################
# BEGIN: OS X files to ignore
#############################
# FROM https://github.com/github/gitignore/blob/master/Global/macOS.gitignore

*.DS_Store
.AppleDouble
.LSOverride

# Icon must end with two \r
Icon


# Thumbnails
._*

# Files that might appear in the root of a volume
.DocumentRevisions-V100
.fseventsd
.Spotlight-V100
.TemporaryItems
.Trashes
.VolumeIcon.icns
.com.apple.timemachine.donotpresent

# Directories potentially created on remote AFP share
.AppleDB
.AppleDesktop
Network Trash Folder
Temporary Items
.apdisk
###########################
# END: OS X files to ignore
###########################

##############################
# BEGIN: Linux files to ignore
##############################
# FROM https://github.com/github/gitignore/blob/master/Global/Linux.gitignore

*~

# temporary files which can be created if a process still has a handle open of a deleted file
.fuse_hidden*

# KDE directory preferences
.directory

# Linux trash folder which might appear on any partition or disk
.Trash-*
############################
# END: Linux files to ignore
############################

*.gem
tmp*
/log/

# NOTE: Comments MUST get their own dedicated lines and cannot be shared with that of the file name.
```

## Starting the Git Repository
* Enter the following commands:
```
git add .
git commit -m "Initial commit"
```
* Create a [GitHub](https://github.com/) repository for your gem's source code, and follow the instructions for pushing the code you've written so far.  Do not add a README file, a .gitignore file, or a license, because you already took care of these details.
