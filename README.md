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
- Find out space taken by docker images, type next line plus the path returned from last commands, example sudo du -sh /var/lib/docker/?
``` ruby
sudo du -sh
```
- Following this daigram, create 3 directories - jenkins/jenkins-data/jenkins_home
![image](https://user-images.githubusercontent.com/99705293/231308698-2530d913-963e-4c27-862a-ce0b1b78dc66.png)

- In 'jenkins-data' create a file called 'docker-compose.yml with your favourite editor, and paste the next script:
``` ruby
version: '3' 
services: 
  jenkins:
    container_name: jenkins 
    image: jenkins/jenkins 
    ports:
      - "8080:8080" 
    volumes:
      - $PWD/jenkins_home:/var/jenkins_home 
    networks:
      - net
networks:
  net:
```
- Give user the ownership:
``` ruby
sudo chown 1000:1000 jenkins_home/
```
- Run your docker-compose file:
``` ruby
docker-compose up -d
```
- To visit the jenkin container through browser, type your local server's IP followed by. :8080.


[![](https://img.shields.io/badge/github-blue?style=for-the-badge)](https://github.com/OmarWarsame)
[![](https://img.shields.io/badge/book-blueviolet?style=for-the-badge)](https://hamzamohdzubair.github.io/redant/)
[![](https://img.shields.io/badge/API-yellow?style=for-the-badge)](https://docs.rs/crate/redant/latest)
[![](https://img.shields.io/badge/Crates.io-orange?style=for-the-badge)](https://crates.io/crates/redant)
[![](https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge)](https://www.linkedin.com/in/owarsame?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BSOodhTsXT4CPjEe8q6c1Aw%3D%3D)





