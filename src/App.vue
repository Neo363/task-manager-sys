<template>
  <div class="container">
    <Header 
      @toggle-add-task="toggleAddTask" 
      :showAddTask="showAddTask"
      title="Task Manager"
    >
    </Header>

    <AddTask v-show="showAddTask" @add-task="addTask"/>

    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => 
        task.id === id ? {...task, reminder: !task.reminder} : task
      ) 
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
  },
  created () {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 3:00pm',
        reminder: true
      },
      {
        id: 2,
        text: 'Friends Gathering',
        day: 'March 4th at 1:00pm',
        reminder: false
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,600;1,400&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
}

.btn {
  display: inline-block;
  border: none;
  padding: 10px 20px;
  font-size: 15px;
  border-radius: 5px;
  margin: 5px;
  color: #fff;
  font-family: 'Poppins', sans-serif;
}
</style>
