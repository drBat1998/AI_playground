Title: my configuaration of the termianl work
tags: #atomic_note #programming 


# Notes
## 1. ~/.zshrc
```shell
nvim ~/.zshrc
```

```shell


# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/opt/anaconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/opt/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/opt/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/opt/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<

if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# Extend PATH
export PATH=~/bin:$PATH
export PATH="/opt/homebrew/opt/openjdk/bin:$PATH" # Add homebrew java to path

export PATH="$HOME/.cargo/bin:$PATH"

# Neovim
alias v=nvim
alias vim=nvim
export VISUAL=nvim
# export EDITOR="$VISUAL"


# Tmux
alias tmux="tmux -f ~/.config/tmux/tmux.conf"


# Git
alias gits='git status'
alias gita='git add -u'
gitm() { git commit -m "$1" }
alias gitp='git push'
alias gitu='git commit -m "Update $(date +%F)"'
alias gitq='git add -u && git commit -m "Update $(date +%F)" && git push'
alias gitc='aicommits' # requires aicommits installed (https://github.com/Nutlope/aicommits)



# Obsidian
alias oo='cd $HOME/second_brain'
alias or='vim $HOME/second_brain/inbox/*.md'




# App shortcuts
alias lg=lazygit
alias leet="nvim leetcode.nvim"

export PATH="$HOME/.local/bin:$PATH"


# Colors
autoload -U colors && colors
setopt prompt_subst

# Git branch function
git_branch() {
  local branch
  branch=$(git symbolic-ref --short HEAD 2>/dev/null)
  [[ -n $branch ]] && echo " $branch"
}

# Git dirty state (✘ if modified)
git_dirty() {
  [[ -n $(git status --porcelain 2>/dev/null) ]] && echo "✘"
}

# Red & black prompt
PROMPT='%F{red}🦇 %n@%m %F{grey}%1~%f $(git_branch) $(git_dirty) %F{red}❯%f '

```

```shell
source ~/.zshrc
```
## 2. tmux
```shell
nvim ~/.tmux.conf
```

```shell
set-option -sa terminal-overrides ",xterm*:Tc"

unbind C-b
set -g prefix C-Space
bind C-Space send-prefix

# Shift arrow to switch windows
bind -n S-Left  previous-window
bind -n S-Right next-window

# Use vim key tom move between panels
bind-key h select-panel -L
bind-key j select-panel -D
bind-key k select-panel -U
bind-key l select-panel -R

# Start windows ķnd panes at 1, not 0
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


source-file ~/.tmux/themes/bloodmoon.tmux



run '~/.tmux/plugins/tpm/tpm'


# set vi-mode
set-window-option -g mode-keys vi
```
## 3. nvim
# Links
[[tmux]]
[[nvim]]
[[zshrc]]