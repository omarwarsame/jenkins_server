![image](https://user-images.githubusercontent.com/99705293/231302990-55732cd7-eea6-4e0c-a5ae-2859452d3721.png)


# Installing Jenkins as a container.
###### Based on Ricardo Andre's 'Jenkins, from zero to hero' course.

There is an assumption that one knows how to use VMs in Virtualbox or VMware applications and that an Ubuntu server with bridge network is already installed.
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
- Give the user the permissions to run docker commands:
``` ruby
sudo usermod -aG docker ${USER}
```
- Check docket daemom status, and it should show 'active':
``` ruby 
sudo systemctl status docker
```
- If it does not show as active, move on to the next step, but chech status again.
- Start docker services and enable it with systemctl:
``` ruby
sudo systemctl start docker
```
- Install docker compose:
``` ruby
sudo apt  install docker-compose
```
- Check that is got installed:
``` ruby
docker compose version
```
- If you get persmission issues, set the permissions with the next line, but check version again to see it got installed properly:
``` ruby
sudo chmod +x /usr/bin/docker-compose
```
- Pull Jenkins container:
``` ruby
docker pull jenkins/jenkins
```
- Where is docker saving images in linux? To know, type:
``` ruby
docker info | grep -i root
```
- Find out space taken by docker images, type next line plus the path returned from last commands, example sudo du -sh /var/.......
``` ruby
sudo du -sh
```







