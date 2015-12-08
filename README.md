## Debian base image generator
Run `sudo sh buildeb.sh` to generate a Debian base image.
It will use `debootstrap`, create a tar-file, generate the `Dockerfile`
and add a SHA256 checksum of the created tar-file to a `ENV` in the `Dockerfile`.
`buildeb.sh` will also add `.git` and any previously generated tar-files
to `.dockerignore`.
  
The generated image will weigh in around 77M compared to the Docker hub library 
version which is around 125M.
  
### Build and verify
`sudo sh buildeb.sh <release> <mirror>`  

For example:
```sh
$ sudo sh buildeb.sh wheezy ftp://ftp.se.debian.org/debian/
$ docker build -t debian -f Dockerfile .
$ docker run -t -i debian cat /etc/debian_version
```  

### Recommended reading  
[Before you initiate a “docker pull”](https://securityblog.redhat.com/2014/12/18/before-you-initiate-a-docker-pull/)  
[Docker Security Cheat Sheet](https://github.com/konstruktoid/Docker/blob/master/Security/CheatSheet.md)  
[Security Vulnerabilities in Docker Hub Images](http://www.infoq.com/news/2015/05/Docker-Image-Vulnerabilities)  
[what does docker.io run -it debian sh run?](https://joeyh.name/blog/entry/docker_run_debian/)  
