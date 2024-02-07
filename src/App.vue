<script >
export default {
  name: "App",
  data() {
    return {
      tasks: [
        {
          text: "Wake up",
          done: true
        },
        {
          text: "Wash your face",
          done: false
        },
        {
          text: "Do a breakfast",
          done: true
        },
        {
          text: "Brush your teeth",
          done: true
        },
        {
          text: "Clean house",
          done: false
        },
        {
          text: "Get dressed",
          done: true
        },
        {
          text: "Go to work",
          done: true
        }
      ]
    }
  },
  methods: {
    eliminateTask(index) {
      this.tasks.splice(index, 1)
    }
  }

}

</script>

<template>
  <h1>Todo List</h1>
  <div class="container">
    <ul v-if="tasks.length != 0">
      <li v-for="(task, index) in tasks">
        <div v-if="task.done" class="barred">
          {{ task.text }} <button @click="eliminateTask(index)"> X </button></div>
        <div v-else class="no_barred">
          {{ task.text }} <button @click="eliminateTask(index)"> X </button> </div>


      </li>
    </ul>
    <ul v-else style="font-size: larger; color: blue; font-weight: bold;">There aren't things to do</ul>
  </div>
</template>

<style ></style>
