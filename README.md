# dfst-docker
Materials for providing Docker containers for the DFST components

The following instructions will (eventually) help you to quickly deploy a set of tools for working with DITA. The goal of these instructions is to get the necessary software infrastrucre deployed as quickly as possible. 

You'll need the following:
- a GNU/Linux server (Ubuntu 14.04, Fedora 21/22, CentOS 7, or CoreOS all support docker) 
- [docker](https://www.docker.com/)

We'll be using the following docker images:
- [BaseX](https://registry.hub.docker.com/u/dirkk/basexhttp/) (image from guy who works at BaseX)
- [Jenkins](https://github.com/docker-library/docs/tree/master/jenkins) (official docker hub image)
- [gitolite](https://registry.hub.docker.com/u/elsdoerfer/gitolite/) or [GitLab](https://registry.hub.docker.com/u/gitlab/gitlab-ce/) (image from GitLab devs), depending on your needs


Hosting services:
- Your own server with docker
- [Digital Ocean](https://digitalocean.com): docker running on Ubuntu 14.04 as a one-click install

Data for the docker applications will be stored at `/srv/<application-name/`.

## Jenkins
```
docker pull jenkins
docker run -p 8080:8080 -v /srv/jenkins:/var/jenkins_home -d jenkins 
# /srv/jenkins needs to be writable by the user jenkins, see 
```

## BaseX
```
docker pull dirkk/basexhttp
# docker run -p 80:8984 --rm -it dirkk/basexhttp:latest # test run
docker run -p 80:8984 -p 1984:1984 --name basexhttp -v /srv/basexhttp/data:/data -v /srv/basexhttp/repo:/repo -v /srv/basexhttp/restxq:/webapp -d dirkk/basexhttp:latest # attach persistent storage & run as daemon
```

## gitolite
```
docker pull elsdoerfer/gitolite
docker run -e SSH_KEY="$(cat ~/.ssh/gitolite.pub)" elsdoerfer/gitolite
```

## GitLab CE
```
docker pull gitlab/gitlab-ce
# The following is all one command:
docker run --detach \
    --publish 8443:443 --publish 8888:80 --publish 2222:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest
```

- You can login to the web interface with username root and password 5iveL!fe (per the GitLab docker instructions).
- Make sure to change the password; GitLab will prompt you before letting you continue
- There may be other things, such as SSL, that you'll want to configure for GitLab, see [https://registry.hub.docker.com/u/gitlab/gitlab-ce/](https://registry.hub.docker.com/u/gitlab/gitlab-ce/)

