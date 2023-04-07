# Ubuntu_Useful_Syntax
Learning skills from daily projects

Unscheduled update

Unzip
======
```
unzip -n src_path -d dest_path
```
-n: extract not existing.

When unzip a very large file(like 30+GB), use this to continue extracting in case of "not enough memory"

-x: dest path

```
zipinfo file_path
```
show details of the zipfile and total number of zip sub files

find
=====
```
find . -type f | wc -l
```
show total number of sub files

Wget
=====
```
wget -O dataset/fma_metadata.zip -nc https://os.unil.cloud.switch.ch/fma/fma_metadata.zip 
```
-O: directed dest, including file name
-nc: not covering existing files

Du
=====
```
du -h --max-depth=1 ~/download
```
show the size of first level foulders

A good way to show google drive folder size in google colab

https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line

Goole Colab
=====
* link to google drive
```
from google.colab import drive
import os
root_path = "/content/drive/MyDrive/dest_path"
drive.mount('/content/drive')
os.chdir(root_path)
```
the bash commands below are now all under root_path
```
!ls
!pwd
!git clone
```

Pip
=====
```
pip show numpy
# or
pip list | grep numpy
```
show package numpy version

Python
=====
```
list(set(A)-set(B))
```
unduplicate list A - unduplicate list B
