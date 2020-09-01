# DNSCrypt-proxy Setting

`sudo pacman -S dnscrypt-proxy`

### Config the dnscrypt-proxy.toml file

`sudo nano /etc/dnscrypt-proxy/dnscrypt-proxy.toml`

#### Note: I'm using NextDNS on dnscrypt-proxy.toml file, so the server_names line looks like this:

* `server_names = ['nextdns']`

#### Setting your IPv4 connection to `127.0.0.1` and (optional `9.9.9.9`) as secondary
* Note: on some OS/Distro use `127.0.2.1`

### Make it work on any new network you connected:

* `sudo nano /etc/resolvconf.conf`

* `name_servers=127.0.0.1`


### Force NetworkManager to using resolvconf
#### Make a new file

* `sudo nano /etc/NetworkManager/conf.d/rc-manager.conf`

#### Add this
```
[main]
rc-manager=resolvconf
```

### Start using DNSCrypt-proxy
* `sudo systemctl enable dnscrypt-proxy.service`

* `sudo systemctl start dnscrypt-proxy.service`

* `sudo systemctl restart NetworkManager.service`


### Additional Command

* `sudo systemctl status dnscrypt-proxy.service`

### or Reboot!
