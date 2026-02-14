Title: you need to learn tmux RIGHT NOW!!
Author: [[NetworkChuck]]
Tags: #youtube #programming 

[[tmux]]
# Notes
```shell
tmux
```

to detach
control+B and then D (D for detach)

to retach
```bash
tmux a
```

3 layers 
1. seassion
2. window
3. panes

name new seseion
```shell
tmux new -s bob
```

to uncover what seseion are running press:
```shell
tmux ls
```

kill session
```bash
tmux kill-session -t bob
```

session with windows
```bash
tmux new -t bob
```
vertical
control+b %

 horizontal
 con+b ""
 
 index windows
 con+b q

windows create
control-b C

windows change
control-b N

rename window 
con-b ,

all things
cont-b W

delete window
cont-b x

copy mode
cont-b [
paste 
c-b ]
# Links
https://youtu.be/nTqu6w2wc68?si=hhXWhka6V0T1jk15