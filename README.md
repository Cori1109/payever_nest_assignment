# PAYEVER | BACK-END ASSIGNMENT

This project was developed after a challenge proposed by Payever for the position of Back-end Engineer. It is a task to create a simple REST application from scratch, using Nest.js, Typescript, MongoDB, RabbitMQ and communicating with an external API (<https://reqres.in/>) .

## Content

[1. Getting Started](#getting-started)  
&emsp;[1.1 Requirements](#requirements)  
[2. Download and Installation](#download-and-installation)    
[3. API Resources](#api-resources)  
&emsp;[3.1 Endpoints](#endpoints)  
[4. Automated Tests](#automated-tests)  
[5. Technologies](#technologies)  
[6. Acknoledments](#acknoledgments)   

## Getting Started

The following instructions will help you get a copy of this project up and running on your local machine. You will be able to test it as Production or Development mode.

Below you will also find relevant information about the API resources available (its endpoints) as well as the main technologies used to build it.

### Requirements

You need to install the following technologies and run them locally:

- <https://nodejs.org/en/download/> - Node.js
- <https://www.mongodb.com/try/download/community> - MongoDB
- <https://www.rabbitmq.com/download.html> - RabbitMQ

PS.: For MongoDB, you can use its Atlas service so you don't have to install it on your machine. You can access it on <https://www.mongodb.com/atlas/database>.

## Download and Installation

Make sure you have Git installed on your machine so you can clone this project by running the following command:

``` bash
git clone https://github.com/Cori1109/ng-backend-assignment.git
```

Alternatively, if you are reading this README after downloading the .zip file, you already have all the necessary files in the root folder so you can move along.

To keep using the dependencies in the containers, stop the application container (only the 'app' one) and connect to the other services by modifying the .env.example file as instructed in the file. You can also connect to the dependencies locally on your machine if you want to (MongoDB and RabbitMQ), but you will also have to modify their variable accordingly.

1. Open the *'.env.example'* file and follow the instructions in it.

2. After setting up your environment variables, run ``` npm install ``` to install all dependencies.

3. ```npm run start:dev``` will start up the application using a nest.js script, running on port 3000. From this point on, you can starting sending request or running tests.

## API Resources

You can use an http client to send requests to this application, such as *Insomnia*, *Postman* or even the *Thunder Client* extension in VS Code.

### Endpoints

1. POST /api/users  
This route stores a user entry in the database. After its creation, it sends an email to 'user.email' with a welcome message and also a RabbitMQ event.
2. GET /api/user/{userId}  
This route retrieves data from an external API and returns a user in JSON representation with dummy information.
3. GET /api/user/{userId}/avatar  
This route retrieves an image from the 'user.data' which is a URL at first. After the first request, it stores the image in the File System and generates a hash which is used to name the .jpg file and also the 'user.avatar' value. On following requests, the image is retrieved from the File System.
4. DELETE /api/user/{userId}/avatar  
This route removes the image file from the File System storage and also the 'user.avatar' entry in the database. 

## Automated Tests

You can find test files in this applications that were written to verify the integrity and efficiency of the code and its funcionalities.  

The Unit Test files for each code file can be found right next to it, in the same directory. The Integration Tests consist of a single file called '*users-integration.spec.ts*' inside the '*test*' folder.

In order to run the tests, in any environment you are, just run:

``` bash
npm run test
```

*npm run test:cov* will give you the coverage of unit tests, which for this project is only missing the ones for the *users.service.ts* file methods.

## Technologies  

Main technologies in this project:

- [Node.js](https://nodejs.org/en/) - *A JavaScript runtime built on Chrome's V8 JavaScript engine.*
- [Nest.js](https://nestjs.com/) - *A progressive Node.js framework to build highly scalable and testable applications.*
- [MongoDB](https://www.mongodb.com/) - *A document-oriented database program.*
- [Typescript](https://www.typescriptlang.org/) - *A strongly typed programming language that builds on JavaScript.*
- [RabbitMQ](https://www.rabbitmq.com/) - *An open-source message-broker software.*

## Acknoledgments

I'd like to thank Payever and its representatives for providing me this challenge with a lot of support. This was not a complex project, but some technologies were relatively new to me during development, which took more time than expected.