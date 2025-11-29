# Ex03 To-Do List using JavaScript

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
## HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Modern To-Do List</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="todo-container">
    <h1>My Tasks</h1>

    <ul id="taskList"></ul>

    <div class="add-task-box">
      <input type="text" id="taskInput" placeholder="Add a new task...">
      <button id="addBtn">+</button>
    </div>

    <div class="actions">
      <button id="showAll" class="active">All</button>
      <button id="showActive">Active</button>
      <button id="showCompleted">Completed</button>
      <button id="clearAll">Clear All</button>
    </div>
  </div>

  <script src="todo.js"></script>
</body>
</html>
```

## CSS
```
body {
  margin: 0;
  font-family: 'Segoe UI', sans-serif;
  background: #f5f6fa;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.todo-container {
  background: #fff;
  padding: 25px;
  width: 380px;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
}

h1 {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

.add-task-box {
  display: flex;
  justify-content: space-between;
  margin-bottom: 15px;
}

.add-task-box input {
  flex: 1;
  padding: 10px;
  border: 2px solid #ddd;
  border-radius: 10px;
}

.add-task-box button {
  margin-left: 10px;
  width: 40px;
  height: 40px;
  font-size: 20px;
  background: #4CAF50;
  color: white;
  border: none;
  border-radius: 50%;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
}

ul li {
  background: #f0f0f0;
  margin: 8px 0;
  padding: 12px;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

ul li.completed {
  text-decoration: line-through;
  background: #d7ffd7;
}

.actions {
  display: flex;
  justify-content: space-between;
  margin-top: 15px;
}

.actions button {
  flex: 1;
  margin: 3px;
  padding: 8px;
  border: none;
  border-radius: 8px;
  background: #eee;
  cursor: pointer;
}

.actions button.active {
  background: #4CAF50;
  color: white;
}
```

## JS
```
document.addEventListener("DOMContentLoaded", () => {
  const taskInput = document.getElementById('taskInput');
  const addBtn = document.getElementById('addBtn');
  const taskList = document.getElementById('taskList');
  const showAll = document.getElementById('showAll');
  const showActive = document.getElementById('showActive');
  const showCompleted = document.getElementById('showCompleted');
  const clearAll = document.getElementById('clearAll');

  let tasks = [];
  let filter = "all";

  addBtn.addEventListener("click", addTask);
  clearAll.addEventListener("click", () => { tasks = []; renderTasks(); });

  [showAll, showActive, showCompleted].forEach(button => {
    button.addEventListener("click", () => {
      [showAll, showActive, showCompleted].forEach(b => b.classList.remove('active'));
      button.classList.add('active');
      filter = button.id === 'showActive' ? 'active' :
               button.id === 'showCompleted' ? 'completed' : 'all';
      renderTasks();
    });
  });

  function addTask() {
    const text = taskInput.value.trim();
    if (!text) return;
    tasks.push({ text, completed: false });
    taskInput.value = "";
    renderTasks();
  }

  function toggleTask(index) {
    tasks[index].completed = !tasks[index].completed;
    renderTasks();
  }

  function deleteTask(index) {
    tasks.splice(index, 1);
    renderTasks();
  }

  function renderTasks() {
    taskList.innerHTML = "";
    tasks.forEach((task, index) => {
      if (filter === 'active' && task.completed) return;
      if (filter === 'completed' && !task.completed) return;

      const li = document.createElement("li");
      li.className = task.completed ? "completed" : "";

      const span = document.createElement("span");
      span.textContent = task.text;
      span.addEventListener("click", () => toggleTask(index));

      const delBtn = document.createElement("button");
      delBtn.textContent = "✖";
      delBtn.addEventListener("click", () => deleteTask(index));

      li.appendChild(span);
      li.appendChild(delBtn);
      taskList.appendChild(li);
    });
  }
});

```

## OUTPUT

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b4678f91-937b-42ef-8dfc-8b6c8217bf53" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/83deba3b-ac02-4daf-8f33-c3df241d1cc2" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
