https://github.com/user-attachments/assets/2965a011-1438-4aff-b098-80a99d03e565
The code for the above video:
index.html :
<!DOCTYPE html>
<html lang="en">
<head>
    <link rel="stylesheet" href="style.css">
    <title>To-Do List</title>
</head>
<body>
    <div class="container">
        <h2>My Tasks</h2>
        <input type="text" id="taskInput" placeholder="Add a new task...">
        <button onclick="addTask()">Add</button>
        <ul id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>[index.html](https://github.com/user-attachments/files/28941150/index.html)

script.jss :
[script.js](https://github.com/user-attachments/files/28941177/script.js)
const taskInput = document.getElementById('taskInput');
const taskList = document.getElementById('taskList');


function addTask() {
    const text = taskInput.value;
    if (text === "") return;

    const li = document.createElement('li');
    li.innerHTML = `${text} <button onclick="this.parentElement.remove()">Delete</button>`;
    taskList.appendChild(li);
    
    taskInput.value = "";
    saveData();
}

function saveData() {
    localStorage.setItem("tasks", taskList.innerHTML);
}


function loadData() {
    taskList.innerHTML = localStorage.getItem("tasks") || "";
}

loadData();
