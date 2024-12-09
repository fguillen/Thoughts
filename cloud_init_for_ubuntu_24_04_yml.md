---
title: cloud_init_for_ubuntu_24_04_yml
description: Cloud config for a Hetzner instance
published: true
date: 2024-12-09T13:03:19.693Z
tags: dev
editor: markdown
dateCreated: 2024-12-09T12:09:57.562Z
---

cloud-init.yml For Ubuntu 24.04

```
#cloud-config
users:
  - name: td
    ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAyQ+kmi25GL1OfxHzzKDcutSVCYLe+fE/SjDWlMuSeEj0ttOb8Hy+gY269hNdnkyG3U4eYh2SSsGUef4JbAfzdab3rNMQiOSHH/ivb5yyrF+vlsFACFQiScyxrzXJNp7Ah6CSPdGE5qtDwgASRzSspMhsGJGuhfa1dXprsDXL/CAkJmpHyd4WYE7hgBd8Dk/jx8MLrqWhrBfzhwEBBf9/GSV1TSwrsEj8EbVATQdXlcEi2RfOMRJvlAV0xovf3Q9kf2qOqtZwt6/bnp6ucsHkND4PNV901tF6Oe0wxWuvTBYnSHmYgbE5lmrAae1k00euAc4HYOftzIE/VOTgiaMiSQ== fguillen.laptop
    sudo: ALL=(ALL:ALL) ALL
    groups: sudo
    shell: /bin/bash
chpasswd:
  expire: true
  users:
    - name: td
      password: changeme
      type: text
runcmd:
  - sed -i -e '/^\(#\|\)PermitRootLogin/s/^.*$/PermitRootLogin without-password/' /etc/ssh/sshd_config
  - sed -i -e '/^\(#\|\)PubkeyAuthentication/s/^.*$/PubkeyAuthentication yes/' /etc/ssh/sshd_config
  - sed -i -e '/^\(#\|\)PasswordAuthentication/s/^.*$/PasswordAuthentication no/' /etc/ssh/sshd_config
  - systemctl restart sshd
  - echo "\$nrconf{kernelhints} = -1;" > /etc/needrestart/conf.d/99disable-prompt.conf
  - apt update
  - apt upgrade -y --allow-downgrades --allow-remove-essential --allow-change-held-packages
  - date > /var/log/cloud_config_setup.log 
  - reboot
```

