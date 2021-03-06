---
layout: default
title: 'Know Your Hobby-App'
parent: Cloud applications
nav_order: 2
modifiedDate: 2019-01-19
comments: true
dateWidget:
    targetTitle: Basic Architecture
    targetDate: 2-Jul-2019
---


# Know Your Hobby: Application Implementation Details

{% include counter-widget.html %}

This application is implemented using cloud infrastructure like, Compute engine for hosting code, Cloud storage for static files and Mongodb Atlas as database
[Application URL](http://23.251.145.189/).

## Dev Process

Source code: [github url: github.com/cafeadmin/blogs.git](https://github.com/cafeadmin/blogs.git)  
Dontnet core version 2.2 is required

## Database: MongoDb Atlas

```javascript
url: mongodb+srv://adyarcafe:<password>@knowyourhobby-stjiv.gcp.mongodb.net/test?retryWrites=true&w=majority
username: adyarcafe@gmail.com
Site password: complex one
<password> for url: random generated
```

Database:  knowYourHobby  

This is in Free Tier.

## Static file Storage

### Google Cloud Storage

Project: KnowYourHobby  
Bucket Name: kyh-stamps  
Files are just referred in posts using url(Need to learn more on this)

## Publishing Details

### Server

Google Cloud Compute instance on Linux 19.04 minimal with .6 GB RAM and 10 GB Memory
Account: AdyarCafe  
Project: KnowYourHobby  
Connect using SSH Putty, Google Cloud Console.

### Published in Linux as per this blog

[See Scott Hanselmans blog for details on publishing to Linux](https://www.hanselman.com/blog/PublishingAnASPNETCoreWebsiteToACheapLinuxVMHost.aspx)

Currently the process is manually run and its not under the control of supervisor tool.
There were issues in setting the urls using configurations

### Process to publish in Server

Navigate to below folder:

```bash
cd /home/adyarcafe/kyh-source/blogs
```

Get latest from Git

```bash
git pull origin master
```

Then publish using Dotnet

```bash
dotnet restore
dotnet build
dotnet publish --configuration Release
OR
dotnet publish --configuration Release --output /var/kyh-server/
```

Then navigate to folder

```bash
cd /home/adyarcafe/kyh-source/blogs/bin/Debug/netcoreapp2.2/
```

Copy to web folder

```bash
sudo cp -a publish/ /var/kyh-server
```

The Application is run using a service in Systemd.

ngnix Congig file.

```bash
sudo vi /etc/nginx/sites-available/default
```

```bash
sudo systemctl enable kyh-app.service
sudo systemctl start kyh-app.service
sudo systemctl status kyh-app.service
\\To see status
sudo journalctl -fu kyh-app.service
```

for testing purpose
If there are errors related to port, run this command to get the listeners of port

```bash
sudo netstat -lutnp | grep -w '5000'
```

remove unwanted listeners

```bash
sudo kill -9 <process_id>
```
