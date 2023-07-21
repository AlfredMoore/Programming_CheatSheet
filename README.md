# Useful_Syntax
Learning skills from daily projects

Unscheduled update

Ubuntu
=====
Unzip
-----
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
-----
```
find . -type f | wc -l
```
show total number of sub files

Wget
-----
```
wget -O dataset/fma_metadata.zip -nc https://os.unil.cloud.switch.ch/fma/fma_metadata.zip 
```
-O: directed dest, including file name
-nc: not covering existing files

Du
-----
```
du -h --max-depth=1 ~/download
```
show the size of first level foulders

A good way to show google drive folder size in google colab

https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line

nohup
-----
```
nohup [command] &
```
run command in the background

```
ps -ef | grep py_downloader.py
kill <PID>
```
stop that command

System Version
=====
```
cat /etc/issue
cat /etc/os-release
hostnamectl
uname -a
cat /etc/debian_version
```

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

```
pip config list
```
show pip source

Change Source
-----
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# Pip source
# mk ''
# [global]
# index-url = https://mirrors.aliyun.com/pypi/simple/
# 
# [install]
# trusted-host=mirrors.aliyun.com
```

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

```
def function(param_a: str, param_b: np.array) -> dict
```

*args and **kargs
-----
```
input *args, and arg will be a tuple
input **kargs, which should be （karg_1=1, karg_2=2...), and karg will be a dictionary {karg_1: 1, karg_2: 2...}
```

print
-----
```
>>> print('I want to learn %s. How about you?' %'Python')
I want to learn Python. How about you?
>>> print('10 - 23 is %d, not %u' %(-13, 13) )
10 - 23 is -13, not 13
print("{} {}".format("hello", "world")) # No position assignment, deault
'hello world'
print("{1} {0} {1}".format("hello", "world") ) # assigned position
'world hello world'
print(f"mean_reward: {mean_reward:.2f} +/- {std_reward:.2f}")
```

Relatively import
-----
```
from . import module_name                 # same director
from .package_name import module_name     # same director
from .. import module name                # upper director
from ..package_name import module_name    # upper director
```

Super()
-----
```
class A (B):
  def __init___ ():
    super().__init()__
    super().func_of_parent()
```

Python x Bash
-----
```
# os.system()
import os
command = "ls"
a = os.system(command)
# a = 0 if it runs well

# save IP address
# os.popen()  execute the cmd and get the output
import os
cmd = 'hostname -I'
result = os.popen(cmd)
ip_addr = result.readlines()[0].replace(' ','').replace('\n','')
print(ip_addr)
```
numpy
-----
```
np.array.tile(2,2)
# A -> [A A]
#      [A A]
```

Python Virtual Env
=====
```
source virtual_env_path/bin/activate
deactivate
```
activate & deactivate

VScode import unresolved, but can be interpreted.
-----
<https://github.com/microsoft/pylance-release/blob/main/TROUBLESHOOTING.md#unresolved-import-warnings>

Conda
=====
```
conda info
conda info -e
# sudo chmod 600 PATH
conda create -n <env name> python=x.x
conda create --prefix=/var/www/myblog/felixvenv python=3.7.1
conda remove -n <env name>
conda remove --name ENV_NAME --all
```
show env information

show all envs

create a virtual env
```
conda install --yes --file requirements.txt
```
conda install packages in requirement.txt

SSH Connection
=====
```
ssh-keygen -m PEM -t rsa -b 4096
```

When lose connection in a public network, the reason might be the "wireless mode". Try to modify the "wireless mode" to 'IEEE 802.11 b/g'

Change Source
=====
```
# apt source (Raspberry Debian10 Buster)
# /etc/apt/sources.list
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main non-free contrib rpi
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main non-free contrib rpi
# /etc/apt/sources.list.d/raspi.list
deb http://mirrors.tuna.tsinghua.edu.cn/raspberrypi/ buster main ui

# Pip source
# mk ''
# [global]
# index-url = https://mirrors.aliyun.com/pypi/simple/
# 
# [install]
# trusted-host=mirrors.aliyun.com
```
