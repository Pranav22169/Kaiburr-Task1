# Kaiburr Task 1 - Java Backend and REST API

## Overview
This project is a Java Spring Boot REST API that manages "Task" objects.  
Each task represents a shell command that can be executed (simulating execution inside a Kubernetes pod).  
The API allows creating, retrieving, searching, executing, and deleting tasks.  
All data is stored in a MongoDB database.

## Technologies Used
- Java 17 (Eclipse Adoptium JDK)
- Spring Boot 3.x
- MongoDB (local)
- Maven 3.9.11
- Postman (for API testing)

## Project Structure
Kaiburr-Task1/
├── pom.xml
├── mvnw
├── mvnw.cmd
├── .mvn/
├── src/
│ ├── main/
│ │ ├── java/com/kaiburr/task1/
│ │ │ ├── controller/TaskController.java
│ │ │ ├── model/Task.java
│ │ │ ├── model/TaskExecution.java
│ │ │ ├── repository/TaskRepository.java
│ │ │ └── KaiburrTask1Application.java
│ │ └── resources/application.properties
│ └── test/
├── screenshots/
│ ├── 1_put_create_task.png
│ ├── 2_get_all_tasks.png
│ ├── 3_get_search_task.png
│ ├── 4_put_execute_task.png
│ ├── 5_mongodb_verification.png
│ └── 6_delete_task.png
└── README.md


## Setup Instructions

### Prerequisites
Make sure you have:
- Java 17 installed
- Maven 3.9+ installed
- MongoDB running locally at mongodb://localhost:27017

### Steps to Run
1. Clone the repository:
git clone https://github.com/<your-username>/Kaiburr-Task1.git
cd Kaiburr-Task1
2. Run the application: mvn spring-boot:run
3. The application will start on: http://localhost:8080

Create or Update a Task
PUT /tasks
Request Body:
{
"id": "123",
"name": "Print Hello",
"owner": "Pranav",
"command": "echo Hello Kaiburr!"
}

Response:
{
  "id": "123",
  "name": "Print Hello",
  "owner": "Pranav",
  "command": "echo Hello Kaiburr!",
  "taskExecutions": []
}

refer Pictures/1_put_create_task.png

Get All Tasks
GET /tasks
Response:
[
  {
    "id": "123",
    "name": "Print Hello",
    "owner": "Pranav",
    "command": "echo Hello Kaiburr!",
    "taskExecutions": []
  }
]
refer Pictures/2_get_all_tasks.png

Search Tasks by Name
GET /tasks/search?name=Hello

Response:
[
  {
    "id": "123",
    "name": "Print Hello",
    "owner": "Pranav",
    "command": "echo Hello Kaiburr!",
    "taskExecutions": []
  }
]

Refer Pictures/3_get_search_task.png

Execute a Task Command
PUT /tasks/{id}/executions
Example: PUT /tasks/123/executions

Response:
{
  "startTime": "2025-10-16T18:03:25.512Z",
  "endTime": "2025-10-16T18:03:26.615Z",
  "output": "Hello Kaiburr!"
}

refer ictures/4_put_execute_task.png

MongoDB Verification

The data is stored in MongoDB under:
Database: kaiburrdb
Collection: tasks
Example document:
{
  "_id": "123",
  "name": "Print Hello",
  "owner": "Pranav",
  "command": "echo Hello Kaiburr!",
  "taskExecutions": [
    {
      "startTime": "...",
      "endTime": "...",
      "output": "Hello Kaiburr!"
    }
  ]
}
refer Pictures/5_mongodb_verification.png

Delete a Task
DELETE /tasks/{id}
Example: DELETE /tasks/123
Response:
Deleted task with id: 123

Validation and Security
The application validates the command input and prevents unsafe shell operations.
Commands containing ;, &, or | are blocked for security reasons.

MongoDB Configuration
Configured in src/main/resources/application.properties:
spring.data.mongodb.database=kaiburrdb
spring.data.mongodb.uri=mongodb://localhost:27017
server.port=8080

Author
Name: Pranav Biju Nair
Date: October 2025
