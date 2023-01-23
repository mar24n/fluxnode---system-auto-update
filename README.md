# Fluxnode---system-auto-update
## Auto update system for flux nodes operators

Simple bash script to update server OS and postpone reboot (if needed after updates) if node is not in mainatanace window.
Using *Crontab* for autoupdates

## How it works:

It gets the node information using the `flux-cli` getinfo command, which is used to check if the node is running

It calculates the number of blocks for maintenance window

It updates the package list using the `sudo apt update` command and then checks for available updates using the apt list --upgradable command

If updates are available, it upgrades the packages using the `sudo apt upgrade -y` command

It checks if a reboot is required 

If a reboot is required, it checks if the node status is "CONFIRMED" and if the maintenance window is open (i.e. if the number of blocks until maintenance is less than or equal to 20) and if so, it schedules a reboot after a delay of 20 minutes plus the number of minutes until maintenance 

If a reboot is not required, it exits the script

## How to use:

Login to the server using   `ssh` 

download the script `wget `
