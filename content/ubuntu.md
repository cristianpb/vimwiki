# Install

```
sudo apt install nmap stow pass ruby i3 roffi dmenu rofi libinput-tools ranger
```

## Node - NVM

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

install a default node version: `nvm install 10`

## neovim

```
sudo apt install neovim
```

* or get the more recent version from ppa:

```
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt update
sudo apt install neovim
```

## polybar

```
sudo apt install xcb-proto libxcb-util1 libxcb-xkb1 libxcb-xkb-dev libxcb1-dev libxcb-util0-dev libxcb-util-dev libpulse-dev libxcb-ewmh2 libxcb-ewmh-dev libxcb-image0 libxcb-image0-dev libxcb-cursor0 libxcb-cursor-dev libxcb-xrm0 libxcb-xrm-dev libalsaplayer0 libalsaplayer-dev libcurl4 libpulse0 libmpdclient2 libmpdclient-dev libjsoncpp1 libjsoncpp-dev libnl-genl-3-dev libnl-genl-3-200 pkg-config cmake cmake-data libcairo2-dev libcairo2 libiw-dev libiw30 libcurl4-openssl-dev python-xcbgen libasound2 libasound2-dev libxcb-icccm4 libxcb-icccm4-dev libxcb-randr0 libxcb-randr0-dev libcairo2 libxcb-composite0 libxcb-composite0-dev mpd
```

```
git clone https://github.com/polybar/polybar.git
./build.sh
```
