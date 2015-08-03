# dfst-docker
Materials for providing Docker containers for the DFST components

The following instructions will (eventually) help you to quickly deploy a set of tools for working with DITA. The goal of these instructions is to get the necessary software infrastrucre deployed as quickly as possible. 

You'll need the following:
- a GNU/Linux server (Fedora 21/22, CentOS 7, or CoreOS all support docker) 
- docker

We'll be using the following docker images:
- [BaseX](https://github.com/dirkk/docker-basexhttp), [Docker hub](https://registry.hub.docker.com/u/dirkk/basexhttp/)
- [gitolite](https://registry.hub.docker.com/u/elsdoerfer/gitolite/)
- [Jenkins](https://github.com/docker-library/docs/tree/master/jenkins) (official docker image)

Notes:
```
# Jenkins
docker run -p 8080:8080 jenkins
# BaseX
docker pull dirkk/basexhttp
docker run -p 80:8984 --rm -it basexhttp:latest
# gitolite
docker pull elsdoerfer/gitolite
docker run -e SSH_KEY="$(cat ~/.ssh/gitolite.pub)" elsdoerfer/gitolite
```
