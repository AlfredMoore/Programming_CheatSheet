# Useful_Syntax
Learning skills from daily projects

Unscheduled update

Greek Alphabet
-----
[relative link](Greek.md)
[web link]https://github.com/AlfredMoore/Useful_Syntax/blob/main/Greek.md


Ubuntu version cheatsheet
-----
| Lunar Lobster: 23 | Jammy Jellyfish 22 | Focal Fossa 20 | Bionic Beaver 18 | Xenial Xerus 16 | Trusty Tahr 14 |

Ubuntu bash
=====
Unzip
-----
```bash
unzip -n src_path -d dest_path
```
-n: extract not existing.

When unzip a very large file(like 30+GB), use this to continue extracting in case of "not enough memory"

-x: dest path

```bash
zipinfo file_path
```
show details of the zipfile and total number of zip sub files

find
-----
```bash
find . -type f | wc -l
```
show total number of sub files

Copy
-----
```bash
cp /path/to/source /path/to/dest/directory/
```
copy file



Wget
-----
```bash
wget -O dataset/fma_metadata.zip -nc https://os.unil.cloud.switch.ch/fma/fma_metadata.zip 
```
-O: directed dest, including file name
-nc: not covering existing files

Du
-----
```bash
du -h --max-depth=1 ~/download
```
show the size of first level foulders

A good way to show google drive folder size in google colab

https://askubuntu.com/questions/1224/how-do-i-determine-the-total-size-of-a-directory-folder-from-the-command-line

nohup
-----
```bash
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
```bash
cat /etc/issue
cat /etc/os-release
hostnamectl
uname -a
cat /etc/debian_version
```

Goole Colab
=====
* link to google drive
```bash
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
```bash
pip show numpy
# or
pip list | grep numpy
```
show package numpy version

```bash
pip config list
```
show pip source

Change Source
-----
```bash
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
```python
list(set(A)-set(B))
```
unduplicate list A - unduplicate list B

```python
tensorflow.Sequence
np.save(... , allow_tickle=True)
np.load(... , allow_tickle=True)
```
to handle the error of "allow_tickle=False" or "raise pickle.UnpicklingError" in tesorflow.Sequence

```python
from multiprocessing import Pool
from itertools import repeat
p = Pool(8)
p.starmap(func, zip(arg_list, repeat(single_arg)))
```
multithread pool executes multi-arguments function 

```python
isinstance(s, str)
```
check if s is a string or int etc. 

```python
from typing import List, Tuple, Dict
```
indicate data type

```python
def function(param_a: str, param_b: np.array) -> dict
```

*args and **kargs
-----
```python
input *args, and arg will be a tuple
input **kargs, which should be （karg_1=1, karg_2=2...), and karg will be a dictionary {karg_1: 1, karg_2: 2...}
```

print
-----
```python
>>> print('I want to learn %s. How about you?' %'Python')
I want to learn Python. How about you?
>>> print('10 - 23 is %d, not %u' %(-13, 13) )
10 - 23 is -13, not 13
print("{} {}".format("hello", "world")) # No position assignment, deault
'hello world'
txt = "I have {an:.2f} Rupees!"
print(txt.format(an = 4))
print("{1} {0} {1}".format("hello", "world") ) # assigned position
'world hello world'
print(f"mean_reward: {mean_reward:.2f} +/- {std_reward:.2f}")
print("\033[91mHello World!\033[0m")  # prints "Hello World!" in red color
```

Relatively import
-----
```python
from . import module_name                 # same director
from .package_name import module_name     # same director
from .. import module name                # upper director
from ..package_name import module_name    # upper director
```

Super()
-----
```python
class A (B):
  def __init___ ():
    super().__init()__
    super().func_of_parent()
```

tqdm()
-----
```python
# Template
with tqdm(total=args.max_train_steps, desc='PPO Trainning', leave=True, ncols=80, unit='steps', unit_scale=True, colour="red") as pbar:
  Iteration
  pbar.update(n)
```
Where, desc('str'): prefix description of the bar, mininterval/maxinterval(float): min/max updating time, miniters(int/float): min mode, ascii(bool/str): True(ASCII) False(unicode), ncols(int): bar width, nrows(int):  , dynamic_ncols(bool): auto mode, smoothing(float): smooth bar updation, bar_format(str): to customize, position(int): bar position, colour(str): bar color


Python x Bash
-----
```python
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
```python
np.tile( A,(2,2) )
# A -> [A A]
#      [A A]
```

```python
np.concatenate((A,B),axis=0)
```
connect Matrix A and B

matplotlib
-----
```python
fig, ax = plt.subplots()    # fig, axs = plt.subplots(m,n) -> axs[m-1,n-1]
ax.plot(x, A @ theta, label='Estimation', color='red')
ax.scatter(x, y, label='Observation', color='blue', marker='x')
ax.legend()
plt.show()
```

Python Virtual Env
=====
```shell
source virtual_env_path/bin/activate
deactivate
```
activate & deactivate

VScode import unresolved, but can be interpreted.
-----
<https://github.com/microsoft/pylance-release/blob/main/TROUBLESHOOTING.md#unresolved-import-warnings>

Conda
=====
```shell
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
```shell
conda install --yes --file requirements.txt
```
conda install packages in requirement.txt

SSH Connection
=====
```bash
ssh-keygen -m PEM -t rsa -b 4096
```

When lose connection in a public network, the reason might be the "wireless mode". Try to modify the "wireless mode" to 'IEEE 802.11 b/g'

Change Source
=====
```bash
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
