<template>
  <div class="addTaskContainer">
    <div class="formControl">
      <div><label for="taskName">Task</label></div>
      <div><input type="text" name="taskName" v-model="text" required></div>
    </div>

    <div class="formControl">
      <div><label for="dayAndTime">Day & Time</label></div>
      <div><input type="text" name="dayAndTime" v-model="day" required></div>
    </div>

    <div class="formControl">
      <div><label for="reminder">Set Reminder</label></div>
      <div><input type="checkbox" name="reminder" v-model="reminder" required></div>
    </div>

    <div class="form-control">
      <button class="saveTaskButton" @click="handleSaveTask">Save Task</button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'AddTask',
  props: {
    task: Object,
  },
  data() {
    return {
      text: '',
      day: '',
      reminder: false,
    }
  },
  methods: {
    handleSaveTask() {
      const newTask = {
        id: Math.floor(Math.random() * 100000000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask)

      this.text = ''
      this.day = ''
      this.reminder = ''
    }
  }
}
</script>

<style scoped>

  .formControl {
    font-size: 20px;
    margin: 20px 0px 20px 0px;
  }

  .formControl input[type="text"] {
    padding-top: 10px;
    width: 100%;
  }

  .saveTaskButton {
    color: white;
    background-color: black;
    padding: 10px;
    border-radius: 5px;
    border: none;
    width: 100%;
  }
</style>