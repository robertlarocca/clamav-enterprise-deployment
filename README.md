# clamav-enterprise-deployment
A script to deploy Clam AntiVirus with on-access and scheduled filesystem scanning.

## Install
Install the systemd `services` and helper scripts using:
```shell
sudo bash INSTALL
```

## Configure
Edit `/etc/clamav/clamd.conf` with the following settings:
```shell
User root
OnAccessExcludeRootUID true
OnAccessExtraScanning true
OnAccessMountPath /home
OnAccessPrevention true
VirusEvent /usr/local/bin/clamav-notify
```

## Schedule
Edit the root user `crontab` with:
```shell
0 0 * * * /usr/local/bin/clamav-schedule
```

