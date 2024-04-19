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

### Step 2: Create an index.php and create a form

- Create an HTML form to add tasks. The form should submit data using the POST method to the index.php file.

### Step 3: Connect to the database

- Connect to the MySQL database named "todo".

### Step 4: Insert the data entered by the user

- Handle form submission to insert tasks into the database.

### Step 5: Create a table

- Display tasks from the database in a table format.

### Step 6: Delete data from the database

- Handle deletion of tasks from the database.

### See the codes below

Step 1 : 
```sql
CREATE TABLE tasks (
    id INT(11) AUTO_INCREMENT PRIMARY KEY,
    task VARCHAR(255)
);

Step 2: 

```html
<form method="post" action="index.php">
    <!-- Display errors if any -->
    <?php if(isset($errors)){ ?>
        <p><?php echo $errors; ?></p>
    <?php } ?>

    <!-- Input field for task -->
    <input autocomplete="off" type="text" name="task" class="task-input">
    
    <!-- Submit button -->
    <button type="submit" class="task_btn" name="submit">Add Task</button>
</form>

Step 3:
```sql
$db = mysqli_connect('localhost', 'root', '', 'todo');

Step 4:
```php
if(isset($_POST['submit'])){
    // Get task from form
    $task = $_POST['task'];

    // Validate task
    if(empty($task)){
        $errors = "You must fill in the task";
    } else {
        // Insert task into database
        mysqli_query($db, "INSERT INTO tasks (task) VALUES ('$task')");
        header('location: index.php');
    }
}

Step 5:
```html
<table>
    <thead>
        <tr>
            <th>N</th>
            <th>Task</th>
            <th>Action</th>
        </tr>
    </thead>
    <tbody>
        <?php $i = 1; while ($row = mysqli_fetch_array($tasks)){ ?>
            <tr>
                <td><?php echo $i; ?></td>
                <td class="task"><?php echo $row['task']; ?></td>
                <td class="delete">
                    <!-- Delete button -->
                    <a href="index.php?del_task=<?php echo $row['id'];?>">x</a>
                </td>
            </tr>
        <?php $i++;  } ?>
    </tbody>
</table>



