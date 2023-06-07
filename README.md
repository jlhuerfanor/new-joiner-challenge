# New joiners challenge 

This challenge was designed to get or increase your knowledge in some specific areas, included but not limited to architectures, solution design, cloud, microservices, frameworks and data base design.  
You will be developing a tool to create, register and manage some of the tasks that a new joiner should work on. 


## First Service 

This service should get a new joiner profile file in pdf or docx format, extract basic information and publish this information into a message broker. 


## Second Service 

This service should get a message from the queue created with the first service and insert it into a database. 

### Endpoints: 

 
- POST /joiner (return 200 or error as needed): Create joiner from data provided in the body of the request 
- PUT /joiner/{joiner _id} (Return updated details of the given joiner): Update provided fields in the body for the given joiner
- GET /joiner/{joiner_id} (Return all joiner information in json)


### Suggested data for the joiners  

 

| Parameter name | Type |
| -------------- | ---- | 
| id | INTEGER | 
| identification_number | INTEGER |
| name | STRING |
| last_name | STRING |
| stack | STRING |
| role | STRING |
| english_level | STRING |
| Domain experience | STRING |

## Third Service

This service should get requests and manage a simple CRUD for the tasks that could be assign to a new joiner, a task could have 1 or more subtask (1 level only) and the status of those inherence subtask will be used to calculate the status of the principal task.

### Endpoints: 

- GET /task (Return a list of all tasks ids) 

Response example: 

[123456789,987654321,123,642375] 

- GET / task /{ task _id} (Return the details of the given task) 

Response example:  

```json
{ 
    " task _id": 34382, 
    "field_2": "string-type-field", 
    "field_3": [“XXX”,”YYY”,”ZZZZ”], 
    "field_4": "?" 
} 
```
- POST /task (return 200 or error as needed): Create task from data provided in the body 
- PUT / task /{ task _id} (Return updated details of the given task): Update provided fields in the body for the given task 
- DELETE / task /{ task _id} (return 200 or error as needed): Delete provided task 


### Suggested data for the tasks 

 
| Parameter name | Type | Default value | 
| -------------- | ---- | ------------- |
| parent_task_id | INTEGER | null |
| id | INTEGER | |
| name | STRING | |
| description | STRING | |
| estimated_required_hours | INTEGER | |
| stack | STRING | |
| min_role | array | |	
 

## Fourth Service 

This service should create a report using csv format and the endpoints exposed by the third service, avoid reading the database directly. 

Generate the following reports in csv files: 

- Top ‘N” joiners by “X” stack (order by amount of task completed) 
- Task completed an uncompleted by joiner 
- Task completed an uncompleted by “X” joiner 
- Days left to complete the tasks by joiner (only for joiners whit unfinished tasks, assume 8 hours 1 day) 

The file generation should be started using a rest endpoint with the appropriate parameters 

 

## General considerations

 

### API

At least level 2 (Maturity Levels of REST API Design) 

### Postman 

Build a postman collection with proper env, routes, variables, etc. configured 

### GIT 

Use a proper git branching strategy, you will be provided with bitbucket credential to develop this challenge. 

## Notes (General) 

- Propose an implement of HPC. 
- You should build 1 service using GO. 
- You should build 1 service using nodejs. 
- The stack for the 2 other services could be chosen by you( maybe python or reutilize one or both of the first 2) 

## Notes (GO)

- Microservices architecture you will need to provide diagram and documentation of your solution design. 
- Unit testing is expected with a coverage of at least 80% on service modules 
- Perform some benchmarking 
- Follow Clean Code principles (Installing any linter, vetter, etc in GoLand can help) 
- Search for Effective Go, Go syntax sugar, Go idioms, etc 
- Follow Go proverbs 
- Use Golang built-in packages, like refelct, http, sql, etc.. 
- Use centralized logger configuration (Keep in mind logging overhead when picking logging libraries) 
- Exploit Golang modularity design (nice directory distribution and module logic, separation of concerns, closures, middlewares, etc.) 
- If possible, try to consider protocol buffers for inter-microservice comms 
- At least one of the services should run outside your machine (Azure, AWS, Heroku, GCP) 
- Swagger. 

## Notes (NodeJS) 

- Express.js 
- Microservices architecture you will need to provide diagram and documentation of your solution design. 
- Unit testing is expected with a coverage of at least 80% on service classes (Jest) 
- Follow Clean Code principles (Installing TsLint in intellij can help) 
- Use typescript 
- At least one of the services should run outside your machine (Azure, AWS, Heroku, GCP) 
- Swagger (plugging to generate node endpoint) 
- Consider the use of pug or any other template engine 

## Notes (Python) 

- Framework could be Flask or Django the architecture should be propose by you 
- Message broker rabitMQ (https://www.rabbitmq.com/tutorials/tutorial-one-python.html) 
- Microservices architecture you will need to provide diagram and documentation of your solution design. 
- Follow Clean Code principles (Installing SonarLint in intellij can help) 
- For Reports we sugest the use of requests, csv, pandas 
- Unit testing is expected with a coverage of at least 80% on service classes (unitest, pytest) 
- pep8 coding standard  
- pycharm, visual code (pylint) 
- bonus point for pythonic coding style 
- Swagger 
- At least one of the services should run outside your machine (Azure, AWS, Heroku, GCP) 

## Notes (Java) 

- Use Spring Framework. 
- Microservices architecture you will need to provide diagram and documentation of your solution design. 
- Unit testing is expected with a coverage of at least 80% on service classes 
- Follow Clean Code principles (Installing SonarLint in intellij can help) 
- Use Lombok to reduce code clutter 
- Use modern code for instance in java Optionals instead of if (x != null), Streams, etc 
- At least one of the services should run outside your machine (Azure, AWS, Heroku, GCP) 
- Swagger 

## Notes (.Net) 

- Microservices architecture you will need to provide diagram and documentation of your solution design. 
- Unit testing is expected with a coverage of at least 80% on service classes (NUnit) 
- Follow Clean Code principles (Installing SonarLint in intellij can help) 
- Use Lombok (or any preferred tool) to reduce code clutter 
- At least one of the services should run outside your machine (Azure, AWS, Heroku, GCP) 
- Broker (Azure Storage Queues, AWS SQS)  
- Suggested Project type project types “Web API REST”, “Reporting Services .Net” or instead “SQL azure reporting power BI”. 
- Database service from azure SQL server or cosmos DB free tier 
- The API documentation could be provided with Swagger 
 