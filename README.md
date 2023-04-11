![image](https://user-images.githubusercontent.com/99705293/231302990-55732cd7-eea6-4e0c-a5ae-2859452d3721.png)


# Installation
###### Based on Ricardo Andre's 'Jenkins, from zero to hero' course.

There is an assumption that one knows how to use VMs in Virtualbox or VMware applications and that an Ubuntu server is already installed.
### Install Docker Engine, containerd, and Docker Compose.

### Install Docker Engine
- Update the apt package index:
``` ruby
sudo apt-get update
```
- To Install the latest Docker Engine, containerd, and Docker Compose, run:

``` ruby
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
- Verify that the Docker Engine installation is successful by running the hello-world image:
``` ruby
sudo docker run hello-world
```




