<!-- TITLE: Developer Setup Guide -->

# Prerequisites
- NodeJS
- Ruby
- SASS Ruby Gem
- Everything in `package.json`
# Setup Steps

First you need to edit `conf/overrides.example.json` and fill in your own overrides. Rename this to overwrite `conf/overrides.json`.

After that all you need to do is type `vagrant plugin install vagrant-hostmanager && vagrant up && vagrant hostmanager`. After that SSH into the box using `vagrant ssh` and export a Consul token by typing `export CONSUL_TOKEN="xxx"`. After that start Gatekeeper by running `cd /vagrant && python3 app.py`. 

You can compile frontend resources by opening two more terminal windows. In the first window run `grunt watch` and in the second one run `grunt`. **You should run these two commands in this order otherwise frontend resources will not be compiled at first.**

If you are having trouble installing the front end dependencies look at the `vagrantfile` for commands to run for SASS etc.

**DO NOT RUN THE FRONTEND COMPILE COMMANDS INSIDE YOUR VAGRANT BOX UNLESS YOU LIKE WAITING!**

Gatekeeper may be accessed at https://auth.dev.bookmarknovels.com.

If you receive an NGINX welcome landing page then run `nginx -s reload` from within your vagrant box and then try again.