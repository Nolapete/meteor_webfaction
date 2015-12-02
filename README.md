# meteor_webfaction
## Instructions for deploying Meteor site to Webfaction hosting

Thanks go out to Racing Tadpole for this post http://racingtadpole.com/blog/meteor-mongodb-webfaction/ which helped me immensely in figuring out deploying on Webfaction.

These instructions update the process with `meteor build <app>`.

Install Mongodb app and note port
(mongodb-linux-x86_64-rhel62-3.0.7 is the version I used per Webfaction support)

Use your version for all commands where appropriate.

Setup Mongodb as per instructions on Webfaction

In an SSH session:
Run mongod as daemon using Fork (https://docs.mongodb.org/manual/tutorial/manage-mongodb-processes/)

In another SSH session:

`$HOME/webapps/mongodb_app_name/mongodb_version/bin/mongo localhost:mongo_port/admin`

Create a user with at least ReadWrite on a new db for your app
Don't use admin db as suggested elsewhere.
See mongodb documention, but basically it is

`use db_name`

`db.create({user: "user_name", pwd: "password, roles: [ { role: "roleName", db: "dbName" }]})`

Install Node.js app using 0.10.xx (Meteor's base supported version) and note port

Upgrade Node.js to Meteor currently supported version per instructions on Webfaction

`meteor build <app>` in your Meteor app's folder then upload the result tar file to `$HOME/webapps/meteor_application_name`

open an SSH session to Webfaction then

`cd $HOME/webapps/meteor_application_name`

`tar -xzf meteor_application_name.tar.gz` that you uploaded

`cd my_directory`

`(cd programs/server && npm install)`

Edit the included start and stop files in this repo replacing the app_names, ports, user_name, password and your_app_url with your own.  This was the hardest part to get working, so enjoy!

Replace your `$HOME/webapps/meteor_app_name/bin` start and stop files with your edited versions.

From a new SSH session:

`cd $HOME/webapps/meteor_app_name`

`./bin/stop`

`./bin/start`

Test your site.
