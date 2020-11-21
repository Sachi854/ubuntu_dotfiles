# README
シェルスクリプトとかも混ざってます  

## Install

```bash
$ cp -r ./ubuntu_dotfiles/. ~/  
$ rm -r ./ubuntu_dotfiles
$ rm -r ./.git
```

# Gen SSH Key

```bash
$ ssh-key -t rsa -b 4096 -C "my_email@tintin.com"
```

## Laptop power optimize

```bash
$ sudo apt update
$ sudo apt install powertop
$ sudo apt install tlp tlp-rdw
$ sudo tlp start
```

## vim commannd

Change mode

```
normal -> instert : I(beginning of line),i(befor cursor),o(next line)
normal -> visual  : v,V
normal -> command : :
other  -> normal  : esc / <C-c>
``` 

mode 

```
# up
k
<C-b> (page up)
gg (first line)

# down
j
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
{ (begin {}block)
} (end {}block)

```

cut/copy/change/other

```

```

