---
layout: post
title:  "Guide to ethereum"
date:   2018-03-11 09:01:57 +0800
categories: [Tool]
icon: icon-html
tags: [blockchain,ethereum]
---
The github address of ethereum is [link][repo_github],I follow the tutorial, it seems that the tutorial is out of date,So I wrote this guide.

### Environment
```
Linux virgilio-X555LB 4.4.0-116-generic 140-Ubuntu SMP  x86_64 x86_64 x86_64 GNU/Linux
pip 9.0.1 from /home/virgilio/.local/lib/python2.7/site-packages (python 2.7)
```
We should install pip before we get started.
```
sudo apt-get -y install python-pip
```

### Installation
#### 1. install Serpent
```
sudo pip install ethereum-serpent
```

#### 2.create a contract
  create a file named mul2.se with the content below:
```
def double(x):
	return(x * 2)
```
#### 3.install pyethereum
  The command blow did not work now.
```
sudo pip install pyethereum #not working now
```
  We should go to [pyethereum][repo_pyethereum] and follow the installation guide
```
sudo apt-get install libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev libyaml-cpp-dev
git clone https://github.com/ethereum/pyethereum/
cd pyethereum
python setup.py install
```
#### 4.execute contract
  Enter to python command tool,end execute code blow
```
from ethereum.tools import tester as t
c = t.Chain()
x= c.contract('mul2.se',language='serpent')
x.double(34)
```
[repo_github]:https://github.com/ethereum/wiki/wiki
[repo_pyethereum]:https://github.com/ethereum/pyethereum


