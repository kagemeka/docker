# Docker Tips



# Forcely remove containers/images
```sh
$ sudo service docker stop
$ cd /var/lib/docker/containers
$ ls # check container ids
$ sudo rm -rf <container id to remove>
$ exit
$ sudo service docker start 
``` 



# Mount AWS S3 bucket as a Volume


1. From IAM console, prepare a user with ability to access s3 programmaticaly.
  - save the information of the user's  `ACCESSKEY` and `SECRET ACCESS KEY`
  - reference
    - https://blog.vizuri.com/practical-persistent-cloud-storage-for-docker-in-aws-using-rexray-pt-1
    - https://tech-blog.s-yoshiki.com/entry/135


2. install a docker plugin `rexray/s3fs`
  - reference  
    - https://hub.docker.com/p/rexray/s3fs

```sh
$ docker plugin install rexray/s3fs \
  S3FS_ACCESSKEY=<AWS user access key> \
  S3FS_SECRETKEY=<AWS user secret access key>
```

3. mount volume 
  - explicit the mount options in docker run command or docker-compose.yml file


- if volumes disappear from `docker volume ls` command's result
```sh
$ docker plugin ls 
$ docker plugin enable <plugin id>
``` 


# start/stop docker 
```sh
# restart docker
$ sudo systemctl restart docker 
# or 
$ sudo service docker stop 
$ sudo service docker start 
```