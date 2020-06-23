**Setup for the project**

1). Create a directory for the projet.
>mkdir directory_name

2). Redirect to it and execute command below:
>npm init

3). Now, you need to install the required packages. In this project, I am using the below packages:

* express.js: It is a web framework.
* mysql: Node.js driver for MySQL
* body-parser: Helps in converting the POST data into the request body.
* nodemon: Helps in automatically restarting the server whenever the code changes.

In order to install these packages, type in the following command.

>npm i --s express express-handlebars mysql body-parser

[What is express handlebars?](https://www.npmjs.com/package/express-handlebars)

Since I want to install nodemon such that it can access any file in the directory, I will be installing it with the global command

>npm i -g nodemon

For the next step, I have used [SQLYog](https://www.webyog.com/) administration tool. Once inside, create a new database with the name **‘learners’**.  Now, within this database, create a new table with the name ‘learnerdetails’ and the following columns:

* learner_id (INT) – Primary Key
* learner_name (VARCHAR)
* learner_email (VARCHAR)
* course_Id (INT) 

Add some data of your own so that we can work on it.

I will be using another application to make my requests called [Postman](https://www.postman.com/). Postman can be easily added to your browser as a plugin. It helps in organizing the requests from the client and store the request history as well.

Now, to retrive all the data inside the table, select GET from the drop-down list and type in the below URL: http://localhost:8080/learners

Subsequesntly, to achieve results, choose POST, PUT and DELETE request from the dropdown and see the reflected data.
