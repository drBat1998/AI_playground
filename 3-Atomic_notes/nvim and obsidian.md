Title: nvim and obsidian
tags: #atomic_note


# Notes
``` shell

if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# Extend PATH
export PATH=~/bin:$PATH
export PATH="/opt/homebrew/opt/openjdk/bin:$PATH" # Add homebrew java to path


# Neovim
alias v=nvim
alias vim=nvim
export VISUAL=nvim
# export EDITOR="$VISUAL"


# Tmux
alias t=tmux


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





# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('/Users/alex/miniforge3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/Users/alex/miniforge3/etc/profile.d/conda.sh" ]; then
        . "/Users/alex/miniforge3/etc/profile.d/conda.sh"
    else
        export PATH="/Users/alex/miniforge3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<


```

# Links