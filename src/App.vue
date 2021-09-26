<template>
  <div class="container">
    <div class="taskTrackerContainer">
      <div class="top">
        <Header 
          @toggle-add-task="toggleAddTask"
          title="Task Tracker"
          :showAddTask="showAddTask"
        />
        <router-view :showAddTask="showAddTask"></router-view>
        <Footer />
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'
import Tasks from './components/Tasks'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Tasks
  },
  data() {
    return {
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
  },
}
</script>

<style>
  body {
    font-family: Arial;
    box-sizing: border-box;
    font-size: 24px;
    margin: 0;
    padding: 0;
  }

  .container {
    border: 1px solid black;
    border-radius: 5px;
    margin: 20px;
  }

  .btn {
    border: none;
    border-radius: 7px;
    color: white;
    font-size: 16px;
    padding: 16px;
  }

  .taskTrackerContainer {
    margin: 40px;
  }
</style>