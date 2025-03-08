# ns8-jellyfin

Jellyfin is a media streaming server.

## Install

Install via Software Center by adding my repo as explained [here](https://repo.mrmarkuz.com)

## Configure

Configure the FQDN and use a certificate. Browse to the set FQDN and setup Jellyfin.

## Upload media

The jellyfin media directory for app instance jellyfin1 is located in

    /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data/

Set owner to be able to read the files:

    chown -R jellyfin1:fellyfin1 /home/jellyfin1/.local/share/containers/storage/volumes/jellyfin-media/_data/*

## Uninstall

To uninstall the instance:

    remove-module --no-preserve jellyfin1

