

<!-- template display -->
<template>
  <div>
    <div class="container">
      <Header @toggle-add-task=" toggleAddTask" title="Task tracker" :boolean="showAddTask" />
      <div v-if="showAddTask">
        <AddTask @add-task ='addTask'/>
      </div>
      
      <TaskItem @toggle-reminder ="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
    </div>
  </div>
</template>

<script>
import AddTask from './components/AddTask';
import Header from './components/Header';
import TaskItem from './components/Task';

export default {
  name: 'App',
  components: {
    Header,
    TaskItem,
    AddTask
  },
  data() {
    return {
      tasks: [], // Initialize tasks as an empty array
      showAddTask:false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask =!this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks,task]
    },
    deleteTask(id) {
      console.log('Deleting task with ID:', id);
      this.tasks = this.tasks.filter(task => task.id !== id);
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=> task.id ==id? {...task,reminder: !task.reminder}:task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Sample Task',
        day: 'March 1 at 2:30pm',
        reminder: true,
      }
      // Add more tasks if needed
    ];
  }
}
</script>


























<!-- css -->
<style>
/* Global styles */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
