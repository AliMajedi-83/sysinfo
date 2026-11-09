# SysInfo Script

A single-file Bash script that prints a complete snapshot of a Linux machine: hardware, CPU, memory, disks, boot mode, battery, SMART health, sensors, and USB devices. Auto-installs missing dependencies across distros.

## Features

- Auto-detects package manager (apt, dnf, yum, pacman, zypper, apk) and installs missing tools
- Full system info via `inxi -F`
- CPU microarchitecture check (x86-64-v2/v3/v4)
- Memory, host info, disk partitions, boot mode (UEFI/BIOS)
- Windows dual-boot detection via `os-prober`
- Free space, battery health (upower), SMART disk health, thermal sensors, USB devices
- Read-only: no system changes except installing missing packages

## Requirements

- bash
- inxi, smartmontools, lm-sensors (auto-installed)
- parted, upower, os-prober (optional/recommended)

## Installation

git clone https://github.com/<your-username>/sysinfo.git
cd sysinfo
chmod +x sysinfo.sh

Optional system-wide install:

sudo cp sysinfo.sh /usr/local/bin/sysinfo
sudo chmod +x /usr/local/bin/sysinfo

## Usage

sudo ./sysinfo.sh

Root is recommended — smartctl, parted, and os-prober need elevated privileges.

Behind a proxy, edit the top of the script:

export http_proxy="http://PROXY_IP:8080"
sudo -E ./sysinfo.sh
