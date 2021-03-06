# docker-proxmox7-ansible

[![Build](https://github.com/nfaction/docker-proxmox7-ansible/actions/workflows/build.yml/badge.svg)](https://github.com/nfaction/docker-proxmox7-ansible/actions/workflows/build.yml)

## Build image manually

Build a container and push it to Docker Hub:

```
docker login
docker build -f Dockerfile -t spikebyte/docker-proxmox7-ansible:latest .
docker push spikebyte/docker-proxmox7-ansible:latest
```

Test container:

```
docker run -it --rm -v $(pwd):/opt/ spikebyte/docker-proxmox7-ansible:latest bash
```

## References

* https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_Buster
* https://pve.proxmox.com/pve-docs/chapter-sysadmin.html#sysadmin_package_repositories
* https://pve.proxmox.com/pve-docs/chapter-pve-installation.html

## Proxmox VE Enterprise

```
cat > /etc/apt/sources.list<< EOF
deb http://ftp.debian.org/debian bullseye main contrib
deb http://ftp.debian.org/debian bullseye-updates main contrib

# security updates
deb http://security.debian.org/debian-security bullseye-security main contrib
EOF

cat > /etc/apt/sources.list.d/pve-enterprise.list<< EOF
deb https://enterprise.proxmox.com/debian/pve bullseye pve-enterprise
EOF

# wget http://download.proxmox.com/debian/proxmox-release-bullseye.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bullseye.gpg
wget https://enterprise.proxmox.com/debian/proxmox-release-bullseye.gpg -O /etc/apt/trusted.gpg.d/proxmox-release-bullseye.gpg
chmod +r /etc/apt/trusted.gpg.d/proxmox-release-bullseye.gpg
```
