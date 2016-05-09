Command-line tools
===

iTerm2
---
* [Homepage](https://iterm2.com)
* [Neutron color schema](https://github.com/mbadolato/iTerm2-Color-Schemes/blob/master/schemes/Neutron.itermcolors)
* [SourceCodePro+Powerline+Awesome+Regular Font](https://github.com/gabrielelana/awesome-terminal-fonts/blob/patching-strategy/patched/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf)
* Config
 * left option key to +Esc
 * Columns=120

NVM
---
* install nvm `git clone https://github.com/creationix/nvm.git ~/.nvm && cd ~/.nvm && git checkout "git describe --abbrev=0 --tags"`

ZSH
---
* on-my-zsh `sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`
* powerlevel9k theme
 * install `git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k)`
 * config (in ~/.zshrc)
 ```
 POWERLEVEL9K_MODE='awesome-patched'
 ZSH_THEME="powerlevel9k/powerlevel9k"
 plugins=(npm nvm git brew)
 export DEFAULT_USER="$USER"
 export NVM_DIR="$HOME/.nvm"
 [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
 POWERLEVEL9K_SHORTEN_DIR_LENGTH=3
 POWERLEVEL9K_SHORTEN_STRATEGY="truncate_middle"
 POWERLEVEL9K_NVM_BACKGROUND="green"
 POWERLEVEL9K_NVM_FOREGROUND="$DEFAULT_COLOR"
 POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(context dir vcs)
 POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status nvm)
 POWERLEVEL9K_STATUS_VERBOSE=false
 ```
