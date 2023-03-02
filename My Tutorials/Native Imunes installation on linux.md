### Install necessary packages
```bash
apt install openvswitch-switch docker.io xterm wireshark \
	make imagemagick tk tcllib util-linux
```


### Change to overlay2 instructions
For performance improvements change docker file system to overlay2

Stop Docker.
```bash
sudo systemctl stop docker
```

Backup contents of /var/lib/docker
```bash
cp -au /var/lib/docker /var/lib/docker.bk
```

Edit /etc/docker/daemon.json to allow overlay2 file system. If the file doesn't exist create it. Add following to it:
```json
{
  "storage-driver": "overlay2"
}
```

Start docker again.
```bash
sudo systemctl start docker
```

Verify the change
```bash
docker info | grep "Storage Driver:"
```
It should now be overlay2
If the above command fails run it with sudo


### Install IMUNES
```bash
git clone https://github.com/imunes/imunes.git
```

```bash
cd imunes
sudo make install
```

For the topologies to work a template filesystem must be created.
```bash
sudo imunes -p
```

IMUNES can now be started by running the imunes command.
```bash
imunes
```

