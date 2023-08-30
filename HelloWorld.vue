<template>
    <div class="todo-app">
    <h1>Todo App</h1>
    <input v-model="newTask" @keyup.enter="addTask" placeholder="Enter a new task">
    <ul>
    <li v-for="(task, index) in tasks" :key="index">
    <input type="checkbox" v-model="task.completed">
    <span :class="{ completed: task.completed }">{{ task.text }}</span>
    <button @click="removeTask(index)">Remove</button>
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
    
    <style scoped>
    .todo-app {
      max-width: 400px;
      margin: 0 auto;
      text-align: center;
      font-family: 'Times New Roman', Times, serif;
    }
    
    ul {
      list-style: square;
      padding: 0;
    }
    
    li {
      display: flex;
      align-items: center;
      justify-content: space-between; /* Add this line */
      margin: 10px 0;
      padding: 10px; /* Add padding */
      border: 1px solid #ccc; /* Add border */
      border-radius: 5px; /* Add border radius */
      background-color: #f9f9f9; /* Add background color */
    }
    
    .completed {
      text-decoration: line-through;
      color: #888;
    }
    
    button {
      padding: 5px 10px;
      background-color: green;
      border: none;
      color: blue;
      cursor: pointer;
      transition: background-color 0.3s ease; /* Add transition */
    }
    
    button:hover {
      background-color: #d32f2f; /* Change color on hover */
    }
    
    input[type="checkbox"] {
      margin-right: 10px;
    }
    
    input[type="text"] {
      padding: 5px;
    }
    </style>
    