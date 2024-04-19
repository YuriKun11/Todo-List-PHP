# Simple To-Do List Web Application Tutorial

This tutorial guides you through creating a simple web application for managing a to-do list. The application will allow users to add tasks, view them in a table, and delete tasks as needed.

## Prerequisites

Before you begin, ensure you have the following:

- Basic knowledge of HTML, PHP, and MySQL.
- A development environment set up with a web server (e.g., Apache), PHP, and MySQL.

## Steps

### Step 1: Create a new database

- Database name: todo
- Table name: tasks
- Number of columns: 2

```sql
CREATE TABLE tasks (
    id INT(11) AUTO_INCREMENT PRIMARY KEY,
    task VARCHAR(255)
);

###Step 2: Create an index.php and create a form
Create an HTML form to add tasks. The form should submit data using the POST method to the index.php file.
