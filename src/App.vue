<script >
export default {
  name: "App",
  data() {
    return {
      new_todo: "",
      error: "",
      to_do: false,
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
      this.tasks.splice(index, 1);
    },
    addTask(text, done) {
      if (this.new_todo.length > 4) {
        this.error = "";
        this.tasks.push({ text, done });
        this.new_todo = "";
      } else {
        this.error = "The task must have al least 5 letters";

      }
    },
    changeDone(value, index) {
      if (value == true) {
        this.tasks[index].done = false
      } else {
        this.tasks[index].done = true
      }
    }
  }
}

</script>

<template>
  <div class="container">
    <div class="card bg-light mb-3">
      <h1 class="card-header">Todo list</h1>
      <div class="card-body">
        <div class="p-2"> <input v-model="new_todo" @keyup.enter="addTask(new_todo, to_do)"> <button
            class="btn btn-primary" @click="addTask(new_todo, to_do)">
            Add
          </button> </div>
        <p style="color: red;"> {{ error }}</p>
        <ul class="list-group" v-if="tasks.length > 0">
          <li class="list-group-item" v-for="(task, index) in tasks">
            <div class="d-flex justify-content-between align-items-center">
              <span :class="{ barred: task.done }" @click="changeDone(task.done, index)">{{ task.text }} </span> <span>
                <button class="btn btn-danger" @click="eliminateTask(index)"> X </button></span>
            </div>


          </li>
        </ul>
        <ul v-else style="font-size: larger; color: blue; font-weight: bold;">There aren't things to do</ul>
      </div>
    </div>
  </div>
</template>

<style ></style>
