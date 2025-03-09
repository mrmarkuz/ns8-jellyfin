# ns8-jellyfin

[Jellyfin](https://jellyfin.org) is a media streaming server.

## Install

Install via Software Center by adding my repo as explained [here](https://repo.mrmarkuz.com)

## Configure

Configure the FQDN and use a certificate. Browse to the set FQDN and setup Jellyfin.

## Upload media

The jellyfin media directory for app instance jellyfin1 is located in

    /home/jellyfin1/.config/state/media

Set owner so the container can read the files:

    chown -R jellyfin1:jellyfin1 /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data/*

Or just login as app user to be able to access the media directory like:

    runagent -m jellyfin1
    ls -l media

It's possible to mount a samba share to media so Jellyfin is able to scan it:

    mount -t cifs -o user=markus@ad.ns8test.com //192.168.0.1/mymusicshare /home/jellyfin1/.config/state/media

## Uninstall

To uninstall the instance:

    remove-module --no-preserve jellyfin1
