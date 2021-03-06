enron-node-mongo
================

A Hortonworks example project for building a simple Node application with Pig, MongoDB, Node.js and the Enron Emails.

Project Setup
=============

Get the Enron Emails
--------------------
An archive of emails from the Enron investigation are available for download on S3 in Avro format https://s3.amazonaws.com/rjurney.public/enron.avro

Installing Pig 0.10
-------------------
You'll need the lastest version of Apache Pig, version 0.10, to use Avro. You can get it here: http://www.apache.org/dyn/closer.cgi/pig

Installing MongoDB
------------------
MongoDB is available for download here: http://www.mongodb.org/downloads 

Installing the MongoDB Java Driver
----------------------------------
The Java driver for MongoDB (which we'll need to connect to it via Pig) is available here: https://github.com/mongodb/mongo-java-driver/downloads 

Installing Node.js
------------------
Node.js is available here: http://nodejs.org/

Connect Node to Mongo
-----------------------------------
`npm install mongodb`

Getting Started
===============

Load the Enron Emails from Avro format into MongoDB
---------------------------------------------------
`pig -l /tmp -x local -v -w -param avros=/me/tmp/enron -param mongourl=mongodb://localhost/enron.emails avro_to_mongo.pig`

Start the Node Application
--------------------------
Our node application is simple: given a message ID, fetch it from MongoDB and display it as JSON. You can take it from here, or use your favorite language. `node email.js`

Display a Message
-----------------
For instance, click on http://localhost:1337/?messageId=%3C3607504.1075843446517.JavaMail.evans@thyme%3E to see the email as JSON. Imagine your own application wrapping your mined data, fresh off Hadoop so easily!

Conclusion
==========

We've used Pig to bridge the gap between Hadoop and Node.js via MongoDB. Pig is fine duct tape.
