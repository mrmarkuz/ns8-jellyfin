# ns8-jellyfin

[Jellyfin](https://jellyfin.org) is a media streaming server.

This app is under heavy development.

## Install

Install via Software Center by adding my repo as explained [here](https://repo.mrmarkuz.com)

## Configure

Configure the FQDN and use a certificate. Browse to the set FQDN and setup Jellyfin.
If you don't see the setup wizard, go to following URL:

    https://jellyfin.domain.tld/web/#/wizardstart.html

If you still can't reach jellyfin, clear the browser cache.

## Media

By default a volume `jellyfin-media` is used to hold the media. This volume is included in the system backup.
You can change the storage path to for example `/mnt/jellyfin` where you can mount the wanted disk or samba/webdav share

## Upload media

The default jellyfin media directory for app instance jellyfin1 is located in

    /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data

Set owner so the container can read the files:

    chown -R jellyfin1:jellyfin1 /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data

It's possible to mount a samba share to media so Jellyfin is able to scan it. The following needs to be executed as root on the host.

    mount -t cifs -o user=markus@ad.ns8test.com //192.168.0.1/mymusicshare /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data

On Rocky I needed to install cifs-utils.

During an app update the media directory gets chowned which doesn't work with a mounted samba share.
So the media dir must not be mounted when updating the app.

## Open points

- Backup only for local media
- Managing mounting different filesystems to Jellyfin media
- Keep mounts during app updates or automatic remounts

## Uninstall

To uninstall the instance:

    remove-module --no-preserve jellyfin1
