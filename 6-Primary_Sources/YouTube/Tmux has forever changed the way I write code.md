Title: Tmux has forever changed the way I write code
Author: [[Dreams of Code]]
Tags: #youtube #programming 

[[tmux]]
# Notes
Tmux package manager
```shell
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

```shell
# tpm plugin
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'
```
tmux + neovim
```shell
set -g @plugin 'christoomey/vim-tmux-navigator'
```
prefix change
```
unbind C-b
set -g prefix C-Space
bind C-Space send-prefix
```
Start windows and panes at 1, not 0
```
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on
```
Shift arrow to switch windows
```
Shift arrow to switch windows
bind -n S-Left  previous-window
bind -n S-Right next-window
```
# Links
https://youtu.be/DzNmUNvnB04?si=ViYR87kDH_C6uXId