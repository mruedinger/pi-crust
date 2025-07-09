# pi-crust

## Goal
The goal of this project is to bootstrap a Raspberry Pi and provide tools to maintain the OS and supporting services. Just as a pie's crust supports its filling - pi-crust lays the foundation for running applications on your pi!

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

The easiest method to flash the OS to your microSD card involves using the [Raspberry Pi Imager tool](https://www.raspberrypi.com/software/).

The tool is pretty intuitive. Make sure to select "Edit Settings" when prompted to "Use OS customisation?" to set up SSH, default username, wifi, and other desired settings.

[Pi docs for the imager tool](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system).

## Run
Prereqs:
* update hosts file
* update vars in services and users roles

Run the setup playbook:
`ansible-playbook -i hosts bake.yml`

Upgrade installed packages:
`ansible-playbook -i hosts upgrade.yml`

Reboot:
`ansible <hostname> -i hosts -b -a "reboot"`
