# pi-crust

## Goal
The goal of this project is to walk through imaging and baseline configuration of a Raspberry Pi.

As it turns out (upon revisiting this after several years), the pi imager tool now takes care of all my personal needs except setting the hostname to match ansible inventory and performing an update & reboot.

I'll keep the old roles and playbooks in this repo in case I find bits of baseline config that are missing over time, but for now, they're no longer needed.

## Equipment
The following hardware was used for this project:
* [Raspberry Pi 3 Model B](https://www.raspberrypi.com/products/raspberry-pi-3-model-b/) (the 3B+ and 4B should also work)
* [Samsung PRO Endurance MicroSD card](https://www.amazon.com/dp/B09W9XYQCQ)
* A MicroSD card reader

I chose the Samsung PRO Endurance because it scored high on the following benchmarks, and was the cheapest of the best options at time of purchase:
https://www.jeffgeerling.com/blog/2019/raspberry-pi-microsd-card-performance-comparison-2019
https://www.tomshardware.com/best-picks/raspberry-pi-microsd-cards

## Image
I previously used Ubuntu Server LTS for my OS, however, I've recently switched to Raspberry Pi OS Lite for app compatibility and feature availability. That said, your Debian based install of choice should likely work fine but may require some config tweaks.

I recommend using the [Raspberry Pi Imager tool](https://www.raspberrypi.com/software/) to flash your SD card with your desired OS.

The tool is pretty intuitive. Make sure to select "Edit Settings" when prompted to "Use OS customisation?" to set up SSH, default username, wifi, and other desired settings.

[Pi docs for the imager tool](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system).

## Run
Prereqs:
* update [hosts](https://github.com/mruedinger/pi-crust/blob/main/ansible/hosts) file
* update the [services](https://github.com/mruedinger/pi-crust/blob/main/ansible/roles/services/vars/main.yml) and [users](https://github.com/mruedinger/pi-crust/blob/main/ansible/roles/users/vars/main.yml) vars if you'll be executing either of those roles

Run configure-pi playbook if you have users or services to set up:
`ansible-playbook -i hosts configure-pi.yml`

Run initialize-pi playbook to upgrade packages:
`ansible-playbook -i hosts initialize-pi.yml`
