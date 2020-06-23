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

4). For the next step, I have used [SQLYog](https://www.webyog.com/). Once inside, create a new database with the name **‘learners’**.  Now, within this database, create a new table with the name ‘learnerdetails’ and the following columns:

* learner_id (INT) – Primary Key
* learner_name (VARCHAR)
* learner_email (VARCHAR)
* course_Id (INT) 

Add some data of your own so that we can work on it.

5). I will be using another application to make my requests called [Postman](https://www.postman.com/). Postman can be easily added to your browser as a plugin. It helps in organizing the requests from the client and store the request history as well.

6). Next, you need to create and run a Stored Procedure in your database which can process your insert or update requests. 

```sql
CREATE DEFINER=`root`@`localhost` PROCEDURE `learnerAddOrEdit`(

IN _learner_id INT,

IN _learner_name VARCHAR(45),

IN _learner_email VARCHAR(45),

IN _course_Id INT

)

BEGIN

IF _learner_id = 0 THEN

INSERT INTO learnerdetails(learner_name,learner_email,course_Id)

VALUES (_learner_name,_learner_email,_course_Id);

SET _learner_id = last_insert_id();

ELSE

UPDATE learnerdetails

SET

learner_name = _learner_name,

learner_email = _learner_email,

course_Id = _course_Id

WHERE learner_id = _learner_id;

END IF;

SELECT _learner_id AS 'learner_id';

END
```

Now, to retrive all the data inside the table, select GET from the drop-down list and type in the below URL: http://localhost:8080/learners

According to our code, learner ID with value 0 indicates that the particular entry is new to the database. So, whenever you are making an Insert request make sure you pass the ID as 0. Now open POSTMAN, select POST from the dropdown list provide the URL and enter learners details in the body section.

Subsequesntly, to achieve results, choose PUT and DELETE request from the dropdown to update and delete records.
