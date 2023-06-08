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

nohup
=====
```
nohup [command] &
```
run command in the background

```
ps -ef | grep py_downloader.py
kill <PID>
```
stop that command

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

```
tensorflow.Sequence
np.save(... , allow_tickle=True)
np.load(... , allow_tickle=True)
```
to handle the error of "allow_tickle=False" or "raise pickle.UnpicklingError" in tesorflow.Sequence

```
from multiprocessing import Pool
from itertools import repeat
p = Pool(8)
p.starmap(func, zip(arg_list, repeat(single_arg)))
```
multithread pool executes multi-arguments function 

```
isinstance(s, str)
```
check if s is a string or int etc. 

Python Virtual Env
=====
```
source virtual_env_path/bin/activate
deactivate
```
activate & deactivate

Conda
=====
```
conda info
conda info -e
conda create -n <env name> python=x.x
conda remove -n <env name>
```
show env information

show all envs

create a virtual env
```
conda install --yes --file requirements.txt
```
conda install packages in requirement.txt
