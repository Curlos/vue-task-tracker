<template>
  <div class="container">
    <Header 
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
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
    display: flex;
    justify-content: center;
    text-align: center;
    border: 1px solid black;
    margin: 20px;
    

  }

  .btn {
    border: none;
    border-radius: 7px;
    color: white;
    font-size: 16px;
    padding: 16px;
  }
</style>