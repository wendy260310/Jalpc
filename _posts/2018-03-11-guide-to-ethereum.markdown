---
layout: post
title:  "Guide to ethereum"
date:   2018-03-11 09:01:57 +0800
categories: block chain 
---
The github address of ethereum is [link][repo_github],I follow the tutorial, it seems that the tutorial is out of date,So I wrote this guide.

### Environment
{% highlight ruby %}
Linux virgilio-X555LB 4.4.0-116-generic 140-Ubuntu SMP  x86_64 x86_64 x86_64 GNU/Linux
pip 9.0.1 from /home/virgilio/.local/lib/python2.7/site-packages (python 2.7)
{% endhighlight %}
We should install pip before we get started.
{% highlight ruby %}
sudo apt-get -y install python-pip
{% endhighlight %}

### Installation
#### 1. install Serpent
{% highlight ruby %}
sudo pip install ethereum-serpent
{% endhighlight %}

#### 2.create a contract
  create a file named mul2.se with the content below:
{% highlight ruby %}
def double(x):
	return(x * 2)
{% endhighlight %}
#### 3.install pyethereum
  The command blow did not work now.
{% highlight ruby %}
sudo pip install pyethereum #not working now
{% endhighlight %}
  We should go to [pyethereum][repo_pyethereum] and follow the installation guide
{% highlight ruby %}
sudo apt-get install libssl-dev build-essential automake pkg-config libtool libffi-dev libgmp-dev libyaml-cpp-dev
git clone https://github.com/ethereum/pyethereum/
cd pyethereum
python setup.py install
{% endhighlight %}
#### 4.execute contract
  Enter to python command tool,end execute code blow
{% highlight ruby %}
from ethereum.tools import tester as t
c = t.Chain()
x= c.contract('mul2.se',language='serpent')
x.double(34)
{% endhighlight %}
[repo_github]:https://github.com/ethereum/wiki/wiki
[repo_pyethereum]:https://github.com/ethereum/pyethereum


