<template>
  <div class="taskContainer" v-bind:class="{complete: reminder, incomplete: !reminder}">
    <div class="top">
      <div>
        <input @click="handleReminder" type="checkbox" v-model="reminder">
        <label for="checkbox" class="checkboxContainer">{{ reminder }}</label>
      </div>
      <i @click="handleDelete" class="fas fa-times"></i>
    </div>
    <div>{{ task.text }}</div>
    <div>{{task.day}}</div>
  </div>
</template>

<script>

export default {
  name: 'Task',
  props: {
    task: Object,
  },
  data() {
    return {
      reminder: this.task.reminder,
    }
  },
  methods: {
    handleReminder() {
      console.log(this.reminder)
      this.$emit('toggle-reminder', this.task.id)
      
    },
    handleDelete() {
      console.log(`deleting ${this.task.id}`)
      this.$emit('delete-task', this.task.id)
    }
  }
}
</script>

<style scoped>

  .taskContainer {
    background-color: rgb(236, 236, 236);
    margin-top: 10px;
    padding: 10px;
    width: 100%;
  }

  .top {
    display: flex;
    justify-content: space-between;
  }

  .fa-times {
    color: red;
  }

  .complete {
    border-left: 10px solid green;
  }

  .incomplete {
    border-left: 10px solid red;
  }
</style>