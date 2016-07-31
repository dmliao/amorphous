---
layout: post
title: Deploying Node.JS with DigitalOcean (2014)
---

_This post was written in 2014, as a series of notes when I was setting up my first server. It's a mess, and it's incomplete, but I keep it here for posterity's sake. The guide offered here may be severely out of date!_


This guide assumes use of Ubuntu 14.04 (latest long term release)

## Initial Setup

### Root setup

Use root to login to the droplet for the first time

    ssh root@<IP ADDRESS>

and then instantly create a new user

    adduser user

Change the user's password (if needed)

    passwd user

and then give the user sudo privileges.

    gpasswd -a user sudo

Switch over to the new user now.

    su - user

### emacs setup

Install emacs

    sudo apt-get update
    sudo apt-get install emacs (whatever the latest version is)

### ssh setup

Open up ssh configuation

    sudo emacs /etc/ssh/sshd_config

The first option that you may want to change is the port that SSH runs on. Find the line that looks like this:

    Port 22

If we change this number to something in between 1025 and 65536, the SSH service on our server will look for connections on a different port. This is sometimes helpful because unauthorized users sometimes try to break into servers by attacking SSH. Changing it forces attackers to figure out which port you're using.

    Port 4444

Next, find the line with:

    PermitRootLogin yes
    
Here, we have the option to disable root login through SSH.  You can modify this line to "no" if you want to disable root login:

    PermitRootLogin no
    
Then restart SSH:

    service ssh restart
    
We do not want to disconnect until we can confirm that new connections can be established successfully. Open up a new terminal and ensure that you can ssh into it (with the correct port, and the non-root user)

    ssh -p 4444 user@SERVER_IP_ADDRESS

## Adding Security

### fail2ban

We can install `fail2ban` to add extra security to login.

    apt-get install fail2ban

Instructions on how to configure `fail2ban` can be found here: [https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04)

### misc.

Refer to [https://www.digitalocean.com/community/tutorials/additional-recommended-steps-for-new-ubuntu-14-04-servers](https://www.digitalocean.com/community/tutorials/additional-recommended-steps-for-new-ubuntu-14-04-servers) for firewall resources and information.

## Installing NodeJS

We have to remove the default node first

    sudo apt-get purge node

Add the node PPA to the system (to get up to date node)

    curl -sL https://deb.nodesource.com/setup | sudo bash -

Then install NodeJS

    sudo apt-get install nodejs
    sudo apt-get install build-essential

At this point, the app can be transferred over to the server via `scp`. For testing purposes, it can be built and run with `node` (or provided npm / grunt scripts).

### Installing PM2

If we just run the app with node, it'll stop when it crashes. We need to do something to prevent that, and we can use PM2 for that.

    npm install pm2 -g

Once the rest of the server has been configured, we can start up the app with PM2 and ensure that it runs and auto-restarts on crashes:

    pm2 start app.js -i max

Make sure to run all preprocessing before starting PM2!

At this point, the app should run.

_Note from 2016: There were some configuration issues with NGINX that I hadn't foreseen when writing this, because some parts of the app in question were served on a static website. [This was the link I used](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-14-04-lts) to help set it up._

