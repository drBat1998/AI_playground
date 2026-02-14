Title: tmux
tags: #atomic_note #programming 

# Basics
Layers:
1. sessions
2. windows (like a tabs)
3. panes (like windows in desktop)

Create a session
``` shell
tmux ls
```

```shell
tmux attach -t name
```
to stop all sessions
``` shell
tmux kill-server
```
# shortcuts
The prefix is a combination of keys used before the command; by default prefix is control+B. I use control +space

prefix s - show active sessions

prefix c - create window
prefix n - next window
prefix p - previous window
prefix number - to a specific window
prefix & - delete the window

prefix % - add panes horizontally
prefix " - add panes vertically
prefix and arrows - help move between panes
prefix q - find the number of panes
prefix x - close the panes

prefix `[` - copy mode


# Theme
```shell
brew install --cask font-monaspace-nerd-font font-noto-sans-symbols-2
brew install bash bc coreutils gawk gh glab gsed jq nowplaying-cli
```

## Tokyo Night Theme configuration
https://github.com/janoamaral/tokyo-night-tmux
```
set -g @plugin "janoamaral/tokyo-night-tmux"

set -g @tokyo-night-tmux_transparent 1
set -g @tokyo-night-tmux_date_forma DMY
set -g @tokyo-night-tmux_show_music 1
set -g @tokyo-night-tmux_show_netspeed 1
set -g @tokyo-night-tmux_show_path 1
set -g @tokyo-night-tmux_path_format full
set -g @tokyo-night-tmux_show_hostname 1
f
```

# .config file

``` shell

set-option -sa terminal-overrides ",xterm*:Tc"
set -g mouse on

unbind C-b
set -g prefix C-Space
bind C-Space send-prefix

# Shift arrow to switch windows
bind -n S-Left  previous-window
bind -n S-Right next-window

# Start windows and panes at 1, not 0
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on

# tpm plugin
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'christoomey/vim-tmux-navigator'
set -g @plugin 'tmux-plugins/tmux-yank'

set -g @plugin 'tmux-plugins/tmux-pain-control'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-logging'

# tokyo-night-tmux
set -g @plugin "janoamaral/tokyo-night-tmux"
set -g @tokyo-night-tmux_transparent 0

set -g @tokyo-night-tmux_transparent 0

set -g @tokyo-night-tmux_show_path 1
set -g @tokyo-night-tmux_path_format full
set -g @tokyo-night-tmux_show_hostname 1

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'


# set vi-mode
set-window-option -g mode-keys vi
```

``` shell
tmux source-file ~/.tmux.conf
```
# Links
[[Tmux has forever changed the way I write code]]