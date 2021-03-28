  # DEPLOYING MEAN STACK

  ### Prerequisites
  In order to complete this project we will need an AWS account and a virtual server with Ubuntu Server OS.

  Spin up an EC2 Instance of t2.nano family with Ubuntu Server 20.04 LTS (HVM) image.

![](image1.jpg)
## Task
In this assignment we are going to implement a simple Book Register web form using MEAN stack.

*Step 1: Install NodeJs*

Node.js is a JavaScript runtime built on Chrome’s V8 JavaScript engine. Node.js is used in this tutorial to set up the Express routes and AngularJS controllers.

*Update ubuntu*

`sudo apt update`

*Upgrade ubuntu*

`sudo apt upgrade`

![ubuntu upgrade and update](image2.jpg)

*Install NodeJS*

`sudo apt install -y nodejs`

![Nodejs install](image3.jpg)

*Step 2: Install MongoDB*

MongoDB stores data in flexible, JSON-like documents. Fields in a database can vary from document to document and data structure can be changed over time. For our example application, we are adding book records to MongoDB that contain book name, isbn number, author, and number of pages.

`sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6`

`echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list`

*Install MongoDB*

`sudo apt install -y mongodb`

![Mongodb installation](image4.jpg)

Start The server

`sudo service mongodb start`

Verify that the service is up and running

`sudo systemctl status mongodb`

![Mongodb status](image6.jpg)

*Install [npm]- Node package manager.*

`sudo apt install -y npm`

![npm](image7.jpg)

*Install ‘body-parser package*

We need ‘body-parser’ package to help us process JSON files passed in requests to the server.

`sudo npm install body-parser`

![BodyParser](image8.jpg)

Create a folder named ‘Books’

`mkdir Books && cd Books`

In the Books directory, Initialize npm project

`npm init`

![npm](image9.jpg)

Add a file to it named `server.js`

`vi server.js`

Copy and paste the web server code below into the server.js file.

var express = require('express');
var bodyParser = require('body-parser');
var app = express();
app.use(express.static(__dirname + '/public'));
app.use(bodyParser.json());
require('./apps/routes')(app);
app.set('port', 3300);
app.listen(app.get('port'), function() {
    console.log('Server up: http://localhost:' + app.get('port'));
});


![server.js](image10.jpg)




