# rc files

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [rc files](#rc-files)
  - [Very Basic Profile](#very-basic-profile)
    - [Linux](#linux)
    - [Windows: PS and Windows Terminal](#windows-ps-and-windows-terminal)

<!-- /code_chunk_output -->

## Very Basic Profile
### Linux
When getting a Linux server, `~/.vimrc` it: [.vimrc](./.vimrc), no need for any plugins.
**However, I found that using `wget -qO- https://raw.github.com/ma6174/vim/master/setup.sh | sh -x` from [github.com/ma6174/vim](https://github.com/ma6174/vim) is quite easier and better.**

Then `zsh`:
```
# install zsh (Ubuntu)
apt-get install zsh

# install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

# cat shells
cat /etc/shells

# default shell is zsh
chsh -s /bin/zsh

# create profile
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

# install one plugin : zsh-syntax-highlighting
cd ~/.oh-my-zsh/plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
```
Then, `~/.zshrc`: [.zshrc](./zshrc).

### Windows: PS and Windows Terminal
Following is old version of configuration, see more in [ps/README](./ps/README.md)

Mainly refer to [this article](https://www.bilibili.com/read/cv3878542), in powershell:

# install chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# install oh-my-posh
choco install ConEmu
Install-Module posh-git -Scope AllUsers
Install-Module oh-my-posh -Scope AllUsers

# make profile
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }

# open $PROFILE
notepad $PROFILE

# add those codes in $PROFILE:
Import-Module posh-git
oh-my-posh init pwsh | Invoke-Expression

# oh-my-posh具体安装如下
![image-20220529014254887](https://cdn.jsdelivr.net/gh/darkchoco10099/img/image-20220529014254887.png)
[官网连接：Change your prompt | Oh My Posh](https://ohmyposh.dev/docs/installation/prompt)
![image-20220529014916797](https://cdn.jsdelivr.net/gh/darkchoco10099/img/image-20220529014916797.png)
[官网链接：PowerShell module | Oh My Posh](https://ohmyposh.dev/docs/migrating)

# allow PS with script
set-executionpolicy remotesigned

# in Microsoft Store, install Windows Terminal

# download and install font:
# https://github.com/adam7/delugia-code/releases/download/v1910.04.1/Delugia.Nerd.Font.Complete.ttf

Settings for Windows Terminal: [windows_terminal: settings.json](./windows_terminal/settings.json)

Install two plugins:

# PoShFuck
Set-ExecutionPolicy RemoteSigned iex ((new-object net.webclient).DownloadString('https://raw.githubusercontent.com/mattparkes/PoShFuck/master/Install-TheFucker.ps1'))

# fzf
choco install fzf
Install-Module PSFzf


Then `$PROFILE`: [powershell: Microsoft.PowerShell_profile.ps1n](Microsoft.PowerShell_profile.ps1n).
