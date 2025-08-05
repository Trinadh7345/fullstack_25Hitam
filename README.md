# fullstack_25Hitam
Full stack web development
#Module1 Labs
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title> Full Stack Web Dev Labs</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 30px;
      background: #f4f4f9;
      color: #333;
    }
    section {
      margin-bottom: 50px;
      padding: 25px;
      border-radius: 15px;
      background: #fff;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      color: #2c3e50;
      margin-top: 0;
    }
    input[type="text"] {
      padding: 10px;
      width: 60%;
      margin-right: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      padding: 8px 14px;
      border: none;
      border-radius: 5px;
      background-color: #3498db;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #2980b9;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      padding: 8px;
      margin-bottom: 10px; 
      background: #ecf0f1;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .zoom-image {
      transition: transform 0.3s ease-in-out;
      width: 200px;
      height: 100px;
      border-radius: 10px;
    }
    .zoom-container {
      width: 200px;
      overflow: hidden;
    }
    .zoom-container:hover .zoom-image {
      transform: scale(1.2); /* Zoom in */
    }
    .actions button {
      margin-left: 10px;
      background-color: #2ecc71;
    }
    .actions button.delete {
      background-color: #e74c3c;
    }
    .actions button.edit {
      background-color: #f39c12;
    }
  </style>
</head>
<body>
 
  <!-- Week 1: List Manipulation -->
  <section>
    <h2>Week 1: List Manipulation</h2>
    <input type="text" id="listInput" placeholder="Enter list item">
    <button onclick="addListItem()">Add</button>
    <ul id="listItems"></ul>
    <script>
      function addListItem() {
        const input = document.getElementById("listInput");
        if (input.value.trim()) {
          const li = document.createElement("li");
          
          const textSpan = document.createElement("span");
          textSpan.textContent = input.value;
 
          const delBtn = document.createElement("button");
          delBtn.textContent = "Delete";
          delBtn.className = "delete";
          delBtn.onclick = () => li.remove();
 
          li.appendChild(textSpan);
          li.appendChild(delBtn);
          document.getElementById("listItems").appendChild(li);
          input.value = "";
        }
      }
    </script>
  </section>
 
  <!-- Week 2: Mouse Events -->
  <section>
    <h2>Week 2: Mouse Events</h2>
    <div id="hoverBox" style="width:300px;height:100px;line-height:100px;text-align:center;background:#ddd; margin-bottom: 20px;">
      Hover over me!
    </div>
 
    <div class="zoom-container">
        <img src="https://images.unsplash.com/photo-1465146344425-f00d5f5c8f07?w=600&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8M3x8bmF0dXJlfGVufDB8fDB8fHww" alt="Zoomable Image" class="zoom-image">
    </div>
 
    <script>
      const hoverBox = document.getElementById("hoverBox");
hoverBox.addEventListener("mouseover", () => hoverBox.style.background = "#a29bfe");
hoverBox.addEventListener("mouseout", () => hoverBox.style.background = "#ddd");
    </script>
  </section>
 
  <!-- Week 3: To-Do List with Full DOM Manipulation -->
  <section>
    <h2>Week 3: DOM Manipulation – To Do List</h2>
    <input type="text" id="taskInput" placeholder="Enter task">
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>
    <script>
      function addTask() {
        const taskInput = document.getElementById("taskInput");
        const taskText = taskInput.value.trim();
        if (taskText) {
          const li = document.createElement("li");
          const span = document.createElement("span");
          span.textContent = taskText;
          li.appendChild(span);
 
          const actions = document.createElement("span");
          actions.className = "actions";
 
          const editBtn = document.createElement("button");
          editBtn.textContent = "Edit";
          editBtn.className = "edit";
          editBtn.onclick = () => {
            const newTask = prompt("Edit task:", span.textContent);
            if (newTask !== null) span.textContent = newTask;
          };
 
          const deleteBtn = document.createElement("button");
          deleteBtn.textContent = "Delete";
          deleteBtn.className = "delete";
          deleteBtn.onclick = () => li.remove();
 
          actions.append(editBtn, deleteBtn);
          li.appendChild(actions);
          document.getElementById("taskList").appendChild(li);
          taskInput.value = "";
        }
      }
    </script>
  </section>
 
</body>
</html>
