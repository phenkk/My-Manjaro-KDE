# My Manjaro KDE Settings

# DNSCrypt-proxy Setting

sudo pacman -S dnscrypt-proxy

# Configure the dnscrypt-proxy.toml file with your own config
sudo nano /etc/dnscrypt-proxy/dnscrypt-proxy.toml

# Setting your connection DNS to 127.0.0.1 (or 127.0.2.1 on some platform) and secondary 9.9.9.9 (optional) or make it work on any new network you connected:
sudo nano /etc/resolvconf.conf
name_servers=127.0.0.1

# Force NetworkManager to using resolvconf
# Make a new file
sudo nano /etc/NetworkManager/conf.d/rc-manager.conf

# Add this
[main]
rc-manager=resolvconf

# Additional Command
sudo systemctl enable dnscrypt-proxy.service
sudo systemctl start dnscrypt-proxy.service
sudo systemctl status dnscrypt-proxy.service
sudo systemctl restart dnscrypt-proxy.service
sudo systemctl restart NetworkManager.service

# or Reboot!
