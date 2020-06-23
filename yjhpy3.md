### 第一题: 如何实现30000文件的批量生成

``` python

import random

num = ["%05d" % i for i in range(30000)]
name = ['水果', '蔬菜', '粮油', '肉类']
for i in num:
    a = random.randint(0, 3)
    captcha = hex(random.randint(4581298449, 281474976710655))
    with open('第一题.txt', 'a', encoding='utf-8') as f:
        f.write(i + ' ' + name[a] + ' ' + captcha + '\n')

```

### 第二题: 请举列说明如何使用第三方库实现linux操作系统管理



``` python

"""
答: 使用psutil这个第三方模块实现系统监控,获取CPU信息,获取内存信息
"""

import psutil

# 获取内存信息
print(psutil.cpu_count())
print(psutil.cpu_count(logical=False))
print(psutil.cpu_times())

# 获取内存信息
print(psutil.virtual_memory())
print(psutil.swap_memory())

```


### 第三题: 如何利用python脚本，实现批量文件重命名


``` python

"""
将文件夹内文件 按照文件的创建时间，进行重命名
"""

import os
import time

path = '/home/zzf531/I/test1/'
fl = os.listdir(path)
print(fl)


def format_time(timestamp):
    t = time.localtime(timestamp)
    return time.strftime('%Y-%m-%d_%H:%M:%S', t)


for i in fl:
    t = format_time(os.path.getatime(path + i))
    oldname = path + i
    newname = path + t + '.txt'
    os.rename(oldname, newname)

fl = os.listdir(path)
print(fl)

```



