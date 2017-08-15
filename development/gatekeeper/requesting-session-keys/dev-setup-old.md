<!-- TITLE: Development Setup Guide (Old) -->

This guide is for the current Gatekeeper and will be deprecated as soon as Gatekeeper is moved to use the new Bookmark infrastructure and Vagrant.
# Installing Dependencies
- Python 3 (3.4 preferred)
- NodeJS (6.9.4)
- NPM
- NGINX - [NGINX configuration for Gatekeeper](https://raw.githubusercontent.com/Bookmark-Novels/Resources/master/Configuration%20Files/bookmark-nginx-local.conf)
```
# Install Dependencies
pip install -r requiremnts.txt
npm install
```
# Actually Setting Up
You need a MySQL database instance to use Gatekeeper. Head over to [dev.bookmark](https://dev.bookmark.services) and provision a new MySQL database. Edit the `conf/gatekeeper.json` file so that the database credentials are in line with your provisioned database. Sync your database.

Now you need to prepare your frontend resources. Open a second terminal window and run `grunt watch` inside the Gatekeeper folder. After that, open a third terminal window and run `grunt`. Now you can run Gatekeeper by typing `python3 app.py`. Navigate to `auth.dev.bookmarknovels.com`.