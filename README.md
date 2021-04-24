# Pi-hole in Docker

This is a simple Pi-Hole implementation in Docker that will run on my Pi server.

## Ubuntu server changes

Need to do things somewhat differently on Ubuntu because it has a service called systemd-resolved listening on port 53.

https://github.com/pi-hole/docker-pi-hole/#installing-on-ubuntu

```
sudo sed -r -i.orig 's/#?DNSStubListener=yes/DNSStubListener=no/g' /etc/systemd/resolved.conf

sudo sh -c 'rm /etc/resolv.conf && ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf'

sudo systemctl restart systemd-resolved
```

## Can't start because something else is on a port?

Can see what is listening on what port by doing the following:

```
sudo netstat -tulpn
```
