# Basic setup

## Install Command Line Tools
`xcode-select --install`

## Get iTerm
[Download](https://www.iterm2.com/downloads.html)

## Homebrew
```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
# In new tab, run following to make sure everything works
brew doctor
```

## Python
python should already be installed on your mac (if not use `brew install python`)
```sh
sudo easy_install pip
sudo pip install ipython
```

## Mongo
```
brew install mongodb@3.0 --with-openssl
```
**Ensure version on app servers matches that on localhost**

## Docker
[Docker Latest Stable Release](https://download.docker.com/mac/stable/Docker.dmg)

# Additional iTerm Shell Setup

## Install oh-my-zsh
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Install PowerLevel 9k (best theme for zsh)
```sh
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

## Install the necessary fonts
```sh
git clone https://github.com/powerline/fonts.git
cd fonts
./install.sh
cd ..
rm -rf fonts
```

## Extra glyphs (Github logo, folder icon, etc.)
Install Source Pro Awesome from [here](https://github.com/stefano-meschiari/dotemacs/raw/master/SourceCodePro%2BPowerline%2BAwesome%2BRegular.ttf)

## iTerm profile
Download Cobalt2 color scheme [here](https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Cobalt2.itermcolors)

In iTerm,

Preferences > Profiles > Colors > Color Presets : Import.. (use downloaded Cobalt2.itermcolors)

Preferences > Profiles > Text : Change font to SourceCodePro+Powerline+Awesome Regular

If you have non-ASCII font, change that as well.

## Initialize theme
Add the following to `~/.zshrc` (order matters):
```sh
POWERLEVEL9K_MODE='awesome-patched'
ZSH_THEME="powerlevel9k/powerlevel9k"
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(ram ssh dir virtualenv rbenv vcs)
```

## Useful Plugins (autocomplete, prompts, etc.)
Add the following to `~/.zshrc`:
```sh
plugins=(git osx sublime python pip st web-search last-working-dir jsontools)
```

#### Example: Sublime Text
Use `st [file or directory]` to open with Sublime Text

## Spotify Integration
Add the following to `~/.zshrc`:
```sh
prompt_zsh_showStatus () {
  local color='%F{white}'
  state=`osascript -e 'tell application "Spotify" to player state as string'`;
  if [ $state = "playing" ]; then
    artist=`osascript -e 'tell application "Spotify" to artist of current track as string'`;
    track=`osascript -e 'tell application "Spotify" to name of current track as string'`;
    echo -n "%{$color%}♫  $artist - $track" ;
  fi
}
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status zsh_showStatus)
```

# Miscellaneous

## Allow scrolling in vim
```sh
defaults write com.googlecode.iterm2 AlternateMouseScroll -bool true
```

## Git
#### Local gitignore
```
# Folder view configuration files
.DS_Store
Desktop.ini

# Thumbnail cache files
._*
Thumbs.db

# Files that might appear on external disks
.Spotlight-V100
.Trashes

# Compiled Python files
*.pyc

# Compiled C++ files
*.out

# Application specific files
venv
node_modules
.sass-cache
```
#### Password caching
Enable git password caching to be used by GUI clients (Tower, SourceTree, etc.)
```sh
git config --global credential.helper osxkeychain
```

## [Aerial Screen Saver](https://github.com/JohnCoates/Aerial)

## Vim config
In `~/.vimrc`, add the following:
```sh
syntax on
```
