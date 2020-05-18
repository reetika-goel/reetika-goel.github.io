---
title: "Docker-Twitter API"
date: 2018-11-04
tags: [software engineering]
excerpt: "Software Engineering"
mathjax: "true"
---

## Introduction

The purpose of this project is to create a client application which implements 8 twitter API’s using Docker container framework, on which various components and applications can be deployed. The
application is built around the developer’s Twitter account. The developer initially requests for the authentication key and token from the Twitter account to work with the APIs. Using the same, the
developer can send request to any of the Twitter APIs and receive a response. An HTML page is designed as a part of user interface with CSS styling. The user interface contains a list of the APIs that are
implemented by the team. Each of these APIs have a unique functionality. When the user clicks on any of these API’s, it redirects to a new page which displays the response to the requested API.

## Tools

* Docker Container
* Django Web Framework
* PyCharm Community Edition
* AWS EC2 Server
* Git Repository

## Technologies

* Python
* HTML, CSS

## Architecture Diagram
 
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/ArchT.png" alt="Architecture Diagram">

## Deployment

Create an AWS EC2 instance and ssh to it. Then follow the below steps to install Git, Docker and Docker-Compose on the Linux AWS server.

* Update the installed packages and package cache on your instance
  * $ sudo yum update -y
* Install Git
  * $ sudo yum upgrade
  * $ sudo yum install git
* Download the project code from GitHub
  * $ Git clone https://github.com/vidhishah22/CMPE-272-The-Seekers.git
* Install the most recent Docker Community Edition package.
  * $ sudo yum install -y docker
* Start the Docker service
  * $ sudo service docker start
* Add the ec2-user to the docker group so you can execute Docker commands without using sudo.
  * $ sudo usermod -a -G docker ec2-user
* Log out and log back in again to pick up the new docker group permissions. You can accomplish this by closing your current SSH terminal window and reconnecting to your instance in a new one. Your
new SSH session will have the appropriate docker group permissions.
* Verify that the ec2-user can run Docker commands without sudo
  * $ docker info
* Run this command to download the latest version of Docker Compose:
  * $ sudo curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
* Apply executable permissions to the binary:
  * $ sudo chmod +x /usr/local/bin/docker-compose
* Test the installation
  * $ docker-compose --version
* Once done with the installation, the project can be run on the AWS server using the following command:
  * $ Docker-compose build
  * $ Docker-compose up -d -- To keep the project running on the background
  
## Steps to create a Django project and application

* Create a Django project using the following command:
  * $ django-admin startproject <projectname>
* Create an app within the project:
  *$ python mange.py startapp <appname>
* To run the project:
  * $ python manage.py runserver
* To run the project on a docker container, add the following files to the project.
  * Docker-compose.yml
  * Dockerfile
  * requirements.txt
  
## Website Screenshots

1. HomePage
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Home.png" alt="Home">

2. Get User Tweets
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/User.png" alt="User">

3. Get Mentions Tweets
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Mention.png" alt="Mention">

4. Get ID Based Tweets
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/ID.png" alt="ID">

5. Get Friends
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Friends.png" alt="Friends">

6. Get Followers
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Followers.png" alt="Followers">

7. Account Settings
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Account.png" alt="Account">

8. Twitter Privacy Policy
<img src="{{ site.url }}{{ site.baseurl }}/images/DockerTwitter/Privacy.png" alt="Privacy">

## Links

* [Github](https://github.com/reetika-goel)
* [Youtube](https://youtu.be/z5zCCflalUk)
