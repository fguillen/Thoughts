---
title: Hetzner - Coolify - New Server
description: Instructions of how to create a new server in Hetzner and add it to Coolify
published: true
date: 2024-12-09T15:09:51.086Z
tags: dev
editor: markdown
dateCreated: 2024-12-09T12:42:18.221Z
---


## Hetzner

Location: Falkenstien
Image: Ubuntu
Type: Shared CPU / CX22
Networking: IPv4 and IPv6
SSH Keys: Fguillen laptop, Coolify
Firewall: firewall-22-80-443
Cloud config: https://thoughts.zebra.town/en/cloud_init_for_ubuntu_24_04_yml
Name: PutAName

## Namecheap

Add a new subdomain/domain. For example `mynewserver.zebra.com` IP: (Hetzner server IP)


## Server

Wait some minutes to be give time for all the setup and users are created.

### Users

#### td

Login with the `td` user:

```
ssh td@mynewserver.zebra.town
```

It will ask for the actual password: `changeme`
It will ask for a new password: (1Password `All Servers root and ubuntu users`)


#### root

Add the same password to root:

```
ssh root@mynewserver.zebra.town
passwd
```

Confirm the authorized keys are correct:

```
cat /root/.ssh/authorized_keys 
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCUl9qpgq1x7Jzh8t60ltCD42ixrcPCGiB0slRVzNwefKDHu4VGyiTCXbbUGY6fe7m2Rycf/fSwc9q6lG76isbQO4d+Wj6fdu3af6EcV7i3A/bvdpL2wvd0IooLDmfzls47fEhOZEq70v9T0gCLNwVq4ICYHMo+01za3exLmItLEhBs6fNjsWKIijFz1ccezAVEZ4cgTXatQ7N65fqYniu12+LxnPYFk0e5kxczBW97ZoqHR6SlCar8wAs1r5ibs9xsrG4+nlZ9x9w8FR+i8Vt3qV8ReBJ5TiFGCxQkthGuRvPikLucZdLEQRGIsNTEcTfuLph26qv3eTfp1r8uA1Av coolify
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAyQ+kmi25GL1OfxHzzKDcutSVCYLe+fE/SjDWlMuSeEj0ttOb8Hy+gY269hNdnkyG3U4eYh2SSsGUef4JbAfzdab3rNMQiOSHH/ivb5yyrF+vlsFACFQiScyxrzXJNp7Ah6CSPdGE5qtDwgASRzSspMhsGJGuhfa1dXprsDXL/CAkJmpHyd4WYE7hgBd8Dk/jx8MLrqWhrBfzhwEBBf9/GSV1TSwrsEj8EbVATQdXlcEi2RfOMRJvlAV0xovf3Q9kf2qOqtZwt6/bnp6ucsHkND4PNV901tF6Oe0wxWuvTBYnSHmYgbE5lmrAae1k00euAc4HYOftzIE/VOTgiaMiSQ== fguillen_laptop
```

## Coolify

### Add new server

Servers > Add

- Name
- IP
- User: root
- Private Key: coolify

Next page:

- Wildcard domain: https://zebra.town

Click on `Validate Server & Install Docker Engine`

### Proxy

Replace default for Caddy:

- Server > Proxy > Stop Proxy
- Switch Proxy > Caddy

### Basic resources

#### Glances

(In Namecheap create a CNAME record: glances.mynewserver.zebra.town -> mynewserver.zebra.town)

- Projects > Add
- Name: Glances MyNewServer Server
- Add new Resource > Glances
- Service Stack > Service Name: glances-mynewserver-zebra-town
- Service Stack > Services > Glances > Settings
  - Domains: https://glances.mynewserver.zebra.town
  
Click on `Deploy`

##### Basic Auth

- Services Stack > Edit Compose File

Add this:

```
    labels:
      - caddy_0.basicauth.0_admin=$2a$14$wofV/aIIl4cXi7WazpLT/O7BdZ0Vv1JlakkeylgOfZXSGrEHGqCXa
```

- Restart






