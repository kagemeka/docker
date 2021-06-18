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