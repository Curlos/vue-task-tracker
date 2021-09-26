<template>
  <div class="headerContainer">
    <h3>{{ title }}</h3>
    <Button 
      @btn-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </div>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  computed: {
    
  }
}
</script>

<style scoped>
  .headerContainer {
    display: flex;
    justify-content: space-between;
    width: 40%;
  }
</style>