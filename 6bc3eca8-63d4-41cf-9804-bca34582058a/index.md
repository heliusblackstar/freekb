# Setting up and upgrading Pi-hole

## Summary
You can easily deploy the [Pi-hole](https://pi-hole.net/) software into a Debian Linux VM with these instructions.

## Installation steps
1. Setup a static IPv4 and static [IPv6 address](../78aa9176-0efe-4590-9d61-d2f6bb9bf591/index.md) on your server.
1. Switch to root and install Docker: `sudo su -; apt install docker-compose docker`
1. Create your docker-compose file: `mkdir pihole; cd pihole; nano docker-compose.yml` and paste the "Docker-compose example" from https://hub.docker.com/r/pihole/pihole/ .  The verbiage in the docker-compose.yml file ensures that Docker will always start this container automatically when your server reboots.
1. This step will take some time to run:  `docker-compose up -d`
1. Confirm it is working by quering Pi-hole over IPv6 local loopback: `nslookup google.com ::1`
1. You can access the admin interface at `http://[IPv6-address-of-your-server]/admin` .  Password will have been randomly set and can be seen by running `docker logs pihole | grep random` .  Record this in your password manager.
1. In your network's DHCP server, remove all existing DNS servers and configure the IPv4 address and IPv6 address of your Pi-hole server as your DNS server.

## Upgrading Pi-hole
1. Upgrading Pi-hole involves deleting and re-deploying a new Pi-hole image.  This will probably clear all your existing Pi-hole settings.
1. Change directory into your pihole folder - `cd pihole` .  Confirm you have a "docker-compose.yml" file in this directory (you will if you followed the above instructions).
1. Pull an updated copy of Pi-hole and deploy a fresh Docker image: `docker pull pihole/pihole; docker-compose down; docker-compose up -d`


*** 
_Mandatory_page_footer: This article and the rest of the [FreeKB](../README.md) is dedicated to the public domain via the [Creative Commons CC0](../LICENSE.md)._


