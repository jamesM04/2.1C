<template>
  <div class="todo-app">
  <h1>Todo App</h1>

  <div class ="input-container">
    <span class="input-label">Enter your tasks below</span>
    

  <input class ="task-input" v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
  </div>
  <button class="add-button" @click="addTask">Add Task</button>
  <ul>
  <li v-for="(task, index) in tasks" :key="index">
  <div class="task">
  <input type="checkbox" v-model="task.completed">
  <span :class="{ completed: task.completed }">{{ task.text }}</span>
  
  <button @click="removeTask(index)">Remove</button>

  
  </div>
  </li>
  </ul>
  </div>
 </template>
  
 <script>
 export default {
  data() {
  return {
  newTask: '',
  tasks: [] 
  };
  },
  methods: {
  addTask() {
  if (this.newTask.trim() !== '') {
  this.tasks.push({
  text: this.newTask,
  completed: false
  });
  this.newTask = '';
  }
  },
  removeTask(index) {
  this.tasks.splice(index, 1);
  }
  }
 };
 </script>
  
 <style>
 body {
  background-color: grey;
 }
 </style>

 <style scoped>
 .todo-app {
  max-width: 400px;
  margin: 0 auto;
  text-align: center;
  font-family: Arial;
  padding: 20px; 
 }
  
 ul {
  list-style: none;
  padding: 0;
 }

 .task {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 5px 0; 
  padding: 5px;
  background-color: #f9f9f9;
}
  
 li {
  display: flex;
  align-items: center;
  margin: 10px 0;
 }
  
 .completed {
  text-decoration: line-through;
  color: #888;
 }
  
 button {
  margin-left: 10px;
  padding: 5px 10px;
  background-color: #f44336;
  align-items: center;
  border: none;
  color: white;
  cursor: pointer;
 }

.input-container 
{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  text-align: center;
}

.input-label
{
  font-size: 18px;
  margin-bottom: 50px; 
  margin-top: 20px;
}

.add-button {
  background-color: #4caf50;
  border: none;
  color: white;
  padding: 15px 20px;
  margin-top: 10px; 
  font-size: 16px; 
  cursor: pointer;
  display: block;
  margin: 0 auto; 
}

.task-input {
  width: 70%; /* Adjust the width as needed */
  padding: 15px; /* Increase padding for a larger input box */
  font-size: 16px; /* Adjust the font size as needed */
  border: 2px solid #ccc;
  border-radius: 5px;
  outline: none;
}

.task-input-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

@media (max-width: 768px) {
  .todo-app {
    max-width: 100%; }
}
 </style>
