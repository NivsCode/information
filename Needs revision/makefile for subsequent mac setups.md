```bash
xcode-select --install

softwareupdate --install-rosetta

/bin/bash -c "$(curl -fsSL <https://raw.githubusercontent.com/Homebrew/install/master/install.sh>)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/nivedhithaagovindaraj/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

brew install mysql
brew install google-chrome
brew install visual-studio-code
brew install zoom
brew install docker
brew install tor

brew install --cask iterm2

sh -c "$(curl -fsSL <https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh>)"
git clone --depth=1 <https://github.com/romkatv/powerlevel10k.git> ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc

git clone <https://github.com/zsh-users/zsh-syntax-highlighting.git> ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone <https://github.com/zsh-users/zsh-autosuggestions> ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone <https://github.com/zsh-users/zsh-history-substring-search> ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-history-substring-search
echo "bindkey '^[OB' history-substring-search-down" >>! ~/.zshrc
echo "bindkey '^[OA' history-substring-search-up" >>! ~/.zshrc
brew install --cask todoist
brew install --cask appcleaner
brew install --cask notion
brew install --cask obsidian
brew install --cask signal

defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"
defaults write com.apple.LaunchServices LSQuarantine -bool false
defaults write com.apple.finder ShowPathbar -bool true
defaults write com.apple.finder ShowStatusBar -bool true
defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES
defaults write com.apple.finder QuitMenuItem -bool true
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true

source ~/.zshrc

ssh-keygen -t ed25519 -C "nivedhithaagovindaraj@gmail.com"
git config --global user.name "niv.codes"
git config --global user.email "nivedhithaagovindaraj@gmail.com"
git config --global color.ui true
eval "$(ssh-agent -s)"
touch ~/.ssh/config
echo "Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
  IgnoreUnknown UseKeychain" >>! ~/.ssh/config
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

```bash
plugins=(
  git
  zsh-syntax-highlighting
  zsh-autosuggestions
  zsh-history-substring-search
  vscode
  macos
)
```

```shell
pbcopy < ~/.ssh/id_ed25519.pub
```

```
brew install --cask tor-browser
cd ../..
cd Applications
gpg --auto-key-locate nodefault,wkd --locate-keys torbrowser@torproject.org

```
-   Notes
    -   Check cask source site for each brew install cask
    -   find a way to login with terminal
    -   run iterm2 to set all themes
    -   download kindle, docker
    -   add the ssh key to github





-   [ ] [Configure iterms and vim on mac](https://medium.com/@jeantimex/how-to-configure-iterm2-and-vim-like-a-pro-on-macos-e303d25d5b5c)[https://medium.com/@jeantimex/how-to-configure-iterm2-and-vim-like-a-pro-on-macos-e303d25d5b5c](https://medium.com/@jeantimex/how-to-configure-iterm2-and-vim-like-a-pro-on-macos-e303d25d5b5c)
-   [ ] [](https://medium.com/featurepreneur/guide-to-iterm2-46cd4625d55a)[https://medium.com/featurepreneur/guide-to-iterm2-46cd4625d55a](https://medium.com/featurepreneur/guide-to-iterm2-46cd4625d55a)
-   [ ] [](https://www.logic24by7.com/mac-terminal-complete-set-up-with-iterm2-and-zsh/)[https://www.logic24by7.com/mac-terminal-complete-set-up-with-iterm2-and-zsh/](https://www.logic24by7.com/mac-terminal-complete-set-up-with-iterm2-and-zsh/)
-   [   ] [https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

# Tags
#incomplete 