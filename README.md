Ahh got it — you’re talking about **GitHub Markdown formatting**, not emoji styling 😄

Yes ✅ — what you just showed (with `#`, `##`, `| tables |`, `---`, etc.) **is exactly how proper Markdown formatting works** on GitHub.
The `#` signs define **headers**, the `|` symbols define **tables**, and the `---` lines create **horizontal separators**.

So you want your **Kaiburr Task 1 README** formatted in *that same clean GitHub style* (like Task 4), right?
Here’s your **Task 1 README rewritten perfectly in that format** — no icons, just clear headings, tables, and consistent Markdown:

---

# Kaiburr Task 1 – Java Backend and REST API

This repository contains the backend REST API for the Kaiburr assignment series.
It is built using **Java Spring Boot** and manages **Task** objects that simulate shell command execution within a container-like environment.

---

## ⚙️ Overview

The API allows you to:

1. Create and update tasks
2. Retrieve and search tasks
3. Execute commands
4. Delete tasks

All data is stored in a **MongoDB** database.

---

## 🧠 Technologies Used

| Component    | Technology                         |
| ------------ | ---------------------------------- |
| Language     | **Java 17 (Eclipse Adoptium JDK)** |
| Framework    | **Spring Boot 3.x**                |
| Database     | **MongoDB (Local instance)**       |
| Build Tool   | **Maven 3.9.11**                   |
| Testing Tool | **Postman**                        |

---

## 📁 Project Structure

Refer to `File_Structure.png` for the complete directory layout.

---

## 🧩 Setup Instructions

### Prerequisites

Ensure you have the following installed:

* Java 17
* Maven 3.9+
* MongoDB running locally (`mongodb://localhost:27017`)

---

### Steps to Run

1. **Clone the repository:**

   ```bash
   git clone https://github.com/<your-username>/Kaiburr-Task1.git
   cd Kaiburr-Task1
   ```

2. **Run the application:**

   ```bash
   mvn spring-boot:run
   ```

3. The application will start on
   `http://localhost:8080`

---

## 🧱 API Endpoints

### 1. Create or Update a Task

**PUT /tasks**

**Request Body:**

```json
{
  "id": "123",
  "name": "Print Hello",
  "owner": "Pranav",
  "command": "echo Hello Kaiburr!"
}
```

**Response:**

```json
{
  "id": "123",
  "name": "Print Hello",
  "owner": "Pranav",
  "command": "echo Hello Kaiburr!",
  "taskExecutions": []
}
```

Refer: `Pictures/1_put_create_task.png`

---

### 2. Get All Tasks

**GET /tasks**

**Response:**

```json
[
  {
    "id": "123",
    "name": "Print Hello",
    "owner": "Pranav",
    "command": "echo Hello Kaiburr!",
    "taskExecutions": []
  }
]
```

Refer: `Pictures/2_get_all_tasks.png`

---

### 3. Search Tasks by Name

**GET /tasks/search?name=Hello**

**Response:**

```json
[
  {
    "id": "123",
    "name": "Print Hello",
    "owner": "Pranav",
    "command": "echo Hello Kaiburr!",
    "taskExecutions": []
  }
]
```

Refer: `Pictures/3_get_search_task.png`

---

### 4. Execute a Task Command

**PUT /tasks/{id}/executions**

**Example:**

```bash
PUT /tasks/123/executions
```

**Response:**

```json
{
  "startTime": "2025-10-16T18:03:25.512Z",
  "endTime": "2025-10-16T18:03:26.615Z",
  "output": "Hello Kaiburr!"
}
```

Refer: `Pictures/4_put_execute_task.png`

---

### 5. MongoDB Verification

Data is stored in the **MongoDB** database:

| Property   | Value       |
| ---------- | ----------- |
| Database   | `kaiburrdb` |
| Collection | `tasks`     |

**Example Document:**

```json
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
```

Refer: `Pictures/5_mongodb_verification.png`

---

### 6. Delete a Task

**DELETE /tasks/{id}**

**Example:**

```bash
DELETE /tasks/123
```

**Response:**

```
Deleted task with id: 123
```

---

## 🔒 Validation and Security

* Validates command inputs and blocks unsafe shell operations.
* Commands containing `;`, `&`, or `|` are **rejected** for security reasons.

---

## ⚙️ MongoDB Configuration

Defined in `src/main/resources/application.properties`:

```properties
spring.data.mongodb.database=kaiburrdb
spring.data.mongodb.uri=mongodb://localhost:27017
server.port=8080
```

---

## 👨‍💻 Author

**Name:** Pranav Biju Nair
**Date:** October 2025

---

Would you like me to make a **matching Task 2, 3, and 4 format template** (so all your Kaiburr README files look uniform on GitHub)?
