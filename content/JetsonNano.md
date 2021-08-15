# Jetson Nano tips

## connect using screen

screen /dev/ttyACM0 115200

## Install docker compose

```
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt install python3-pip
sudo apt-get install curl python3-pip libffi-dev python-openssl libssl-dev zlib1g-dev gcc g++ make -y
sudo apt install rustc
sudo pip3 install setuptools-rust
sudo pip3 install docker-compose
```

## Make NVIDIA Jetson Nano Developer Kit Headless

```bash
sudo systemctl stop gdm3
sudo systemctl disable gdm3
sudo systemctl set-default multi-user.target
sudo apt remove --purge ubuntu-desktop gdm3 libreoffice-common chromium-browser whoopsie unattended-upgrades modemmanager
sudo reboot
```

https://devtalk.nvidia.com/default/topic/1048642/jetson-nano/links-to-jetson-nano-resources-amp-wiki/

https://devtalk.nvidia.com/default/topic/1057006/jetson-nano/hello-ai-world-now-supports-python-and-onboard-training-with-pytorch-/

https://devtalk.nvidia.com/default/topic/1049071/jetson-nano/pytorch-for-jetson-nano-version-1-3-0-now-available/
