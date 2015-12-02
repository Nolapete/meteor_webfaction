# meteor_webfaction
## Instructions for deploying Meteor site to Webfaction hosting

Thanks go out to Racing Tadpole for this post http://racingtadpole.com/blog/meteor-mongodb-webfaction/ which helped me immensely in figuring out deploying on Webfaction.

These instructions update the process with `meteor build <app>`.

Install Mongodb app and note port
(mongodb-linux-x86_64-rhel62-3.0.7 is the version I used per Webfaction support)

Use your version for all commands where appropriate.

Setup Mongodb as per instructions on Webfaction

Run mongod as daemon using Fork (https://docs.mongodb.org/manual/tutorial/manage-mongodb-processes/)

Install Node.js app using 0.10.xx (Meteor's base supported version) and note port

Upgrade Node.js to Meteor currently supported version per instructions on Webfaction

`meteor build <app>` in your Meteor app's folder then upload the result tar file to `$HOME/webapps/meteor_application_name`

open an SSH session to Webfaction
`cd $HOME/webapps/meteor_application_name`
`tar -xzf meteor_application_name.tar.gz` that you uploaded

