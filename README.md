# ns8-jellyfin

[Jellyfin](https://jellyfin.org) is a media streaming server.

This app is under heavy development.

## Install

Install via Software Center by adding my repo as explained [here](https://repo.mrmarkuz.com)

## Configure

Configure the FQDN and use a certificate. Browse to the set FQDN and setup Jellyfin.

## Upload media

The jellyfin media directory for app instance jellyfin1 is located in

    /home/jellyfin1/.config/state/media

Set owner so the container can read the files:

    chown -R jellyfin1:jellyfin1 /home/jellyfin1/.config/state/media

Or just login as app user, this way you don't need to set the owner afterwards:

    runagent -m jellyfin1
    ls -l media

It's possible to mount a samba share to media so Jellyfin is able to scan it:

    mount -t cifs -o user=markus@ad.ns8test.com //192.168.0.1/mymusicshare /home/jellyfin1/.config/state/media

During an app update the media directory gets chowned which doesn't work with a mounted samba share.
So the media dir must not be mounted when updating the app. I'm working on other solutions.

## Uninstall

To uninstall the instance:

    remove-module --no-preserve jellyfin1
