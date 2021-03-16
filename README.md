# README
シェルスクリプトとかも混ざってます  

# Install

```bash
$ cp -r ./ubuntu_dotfiles/. ~/  
$ rm -r ./ubuntu_dotfiles
$ rm -r ./.git
```

# Gen SSH Key

```bash
$ ssh-keygen -t rsa -b 4096 -C "my_email@tintin.com"
$ cat < ~/.ssh/id_rsa.pub
$ ssh -T git@github.com
```

# Set proxy

Terminal  
 
```bash
export http_proxy="http://remilia.scarlet-net.ac.jp:3983"
export https_proxy="https://remilia.scarlet-net.ac.jp:3983"
```

git  

```bash
git config --global http.proxy http://remilia.scarlet-net.ac.jp:3983
git config --global https.proxy http://remilia.scarlet-net.ac.jp:3983
```  

apt  
  
```bash
sudo vim /etc/apt/apt.conf

Acquire::http::Proxy "http://foo.com:8080"
Acquire::https::Proxy "http://bar.com:8080"
```  

pip  

```bash
pip3 --proxy=http://username:password@foobar.com:8080 install numpy
```

# Laptop power optimize

```bash
$ sudo apt update
$ sudo apt install powertop
$ sudo apt install tlp tlp-rdw
$ sudo tlp start
```

# Disable C6 States of Zen env

Load msr modules when loading OS

```
sudo vim /etc/modules-load.d/modules.conf 
```

```
msr
```

Auto disable c6 states at boot time

```
git clone https://github.com/joakimkistowski/amd-disable-c6.git
cd amd-disable-c6/
sudo make install
sudo systemctl enable amd-disable-c6.service
sudo systemctl start amd-disable-c6.service
reboot
```

If you want to be disable c6 at one time...

```
git clone https://github.com/r4m0n/ZenStates-Linux.git
cd ZenStates-Linux/
# disable c6
sudo python zenstates.py --c6-disable
# check state
sudo python zenstates.py -l
```

# Change dir lang

```bash
LANG=C xdg-user-dirs-gtk-update
```

# Change audio  sample-format and rate

```
sudo vim /etc/pulse/daemon.conf
```

```
;; default-sample-format = s16le
;; default-sample-rate = 44100
default-sample-format = s24le
default-sample-rate = 96000
```

```
pulseaudio -k
```

# Disable mouse acceleration

GNOME only

```
sudo apt install dconf-editor
```

```
dconf-editor

org/gnome/desktop/peripherals/mouse/acceleration-profile
```

# vim commannd

Change mode  

```bash
normal -> instert : I(beginning of line),i(befor cursor),o(next line)
normal -> visual  : v,V
normal -> command : :
other  -> normal  : esc / <C-c>
``` 

move  

```bash
# up
k
<C-u> (1/2 page up)
<C-b> (page up)
gg (first line)

# down
j
<C-d>
<C-f>
G

# right
l
->
w (end of word)
W (end of wordblock)

# left
h
<-
b
B

# othre
nG (jump to line n)
{ (begin {}block)
} (end {}block)

```

Visual mode  

```bash
# vmode is used for renge selection
v
V (select line)
and use move command
```

cut/copy/change/other  

```bash
# copy == yank
visual mode + y (Range copy)
y  (1 line copy?)
yy (1 line copy)
0y (1 line copy <- index start is 0)
ny (n+1 line copy)
"*y(copy to clipboard)

# delete(cut)
vmode + d
d
dd
0d
nd

# paste
p
0p (register 0)
np (registre n)
"*p(paste from clipboard)
```

seve  

```bash
:w
:w filename.cpp
:q end
:q! force end
:wq
```

search  

```bash
/foobar (search foobar)
+ Enter + n/N -> (other hit)

/\cfoobar (search FOOBAR,fooBAR, foobar....)
+ Enter + n/N -> (other hit)
```

replace  

```bash
r (replace char under cursor)
:%s/foo/bar (replace all foo to bar, but 1 line 1 replace)
:%s/foo/bar/g (replace all foo to bar)
:1,15s/foo/bar/g (replace 1~15 line foo to bar)

regular expresssion...
```

split  

```bash
:sp
:vp

# change tab
<C-w>

# open file
:args filename.txt

# end
:q
```

check diff  

```bash
vim -d a.txt b.txt
```
