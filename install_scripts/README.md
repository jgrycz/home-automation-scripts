# Introduction
This directory contains files used for seting up home assistant on terminal DELL WYSE Dell Z90D7 Zx0 with Debian 10 (Buster) installed.

# Terminal info:
```yaml
wyse:
  model: WYSE Dell Z90D7 Zx0
  cpu:
    clock: 1,4GHz
    type: AMD Embedded G-Series
  ram:
    size: 8GB
    type: DDR3
  ssd:
    model: Crucial BX500
    manufacter_code: CT120BX500SSD1
    size: 120GB
```

# Preconditions
Ansible is used as an autmation tool, before start make sure that ansible is installed, to install ansible please execute:
```bash
$ sudo apt-get update && sudo apt-get install ansible
```

To provide passwordless communication over ssh please execute below command:
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub <terminal ip>
```

# Running playbooks
Installation process is divided into 3 stages:
1. Requirements installation - install_requirements.yaml
2. Docker - install_docker.yaml
3. Install Home Assistant itself

To install all requirements please execute `install_requirements.yaml` playbook as below:
```bash
$ ansible-playbook -i inventory.ini install_requirements.yaml
```

To install Home Assistant please execute below commands:
```bash
sudo curl -Lo installer.sh https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh
sudo bash installer.sh --machine qemux86-64
```
