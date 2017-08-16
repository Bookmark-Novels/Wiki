<!-- TITLE: Developer Setup Guide -->
This guide is for those who are working off of the `dev-react-port` branch.

All you need to do is type `vagrant plugin install vagrant-hostmanager && vagrant up && vagrant hostmanager`. After that SSH into the box using `vagrant ssh` and start Gatekeeper by running `cd /vagrant && python3 app.py`. 

You can compile frontend resources by opening two more terminal windows. In the first window run `grunt watch` and in the second one run `grunt`. **You should run these two commands in this order otherwise frontend resources will not be compiled at first.**