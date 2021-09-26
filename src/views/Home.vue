<template>
  <AddTask v-show="showAddTask" @add-task="addTask" />
  <Tasks
    @toggle-reminder="toggleReminder"
    @delete-task="deleteTask"
    :tasks="tasks"
  />
</template>

<script>
import Tasks from '../components/Tasks'
import AddTask from '../components/AddTask'

export default {
  name: 'Home',
  props: {
    showAddTask: Boolean,
  },
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    async addTask(task) {
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task),
      })

      const data = await res.json()
      this.tasks = [...this.tasks, data]

    },
    async toggleReminder(id) {
      const taskToToggle = await this.fetchTask(id)
      console.log(taskToToggle)
      const toggledTask = {...taskToToggle, reminder: !taskToToggle.reminder}

      const res = await fetch(`api/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(toggledTask),
      })

      const data = await res.json()
      this.tasks = this.tasks.filter((task) => {
        if (task.id === id) {
          return {...task, reminder: data.reminder}
        }
        return (
          task
        )
      })
    },
    async deleteTask(id) {
      const res = await fetch(`api/tasks/${id}`, {
        method: 'DELETE',
        headers: {
          'Content-type': 'application/json',
        },
      })

      const data = await res.json()
      this.tasks = this.tasks.filter((task) => task.id !== id)
      console.log(data)
      return data
    },
    async fetchTasks() {
      const res = await fetch('api/tasks')
      const data = await res.json()
      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)
      const data = res.json()
      return data
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
  }
}


</script>

<style scoped>
</style>