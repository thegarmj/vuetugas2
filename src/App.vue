<script setup>
import { ref, onMounted, computed, watch } from "vue";

const todos = ref([]);
const name = ref("");

const newTask = ref("");
const tasks = ref([]);

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const removeTask = (index) => {
  tasks.value.splice(index, 1);
};
</script>

<template>
  <div id="app">
    <h1>My To-Do List</h1>
    <form @submit.prevent="addTask">
      <h4>What's on your todo list?</h4>
      <input type="text" name="content" id="content" placeholder="Have a nice your day!!" v-model="newTask" />
      <input type="submit" value="Add todo" />
    </form>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
#app {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
}

form {
  margin-bottom: 20px;
}

input[type="text"] {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-bottom: 10px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
}

button {
  padding: 5px 10px;
  background-color: #ff0000;
  color: #fff;
  border: none;
  cursor: pointer;
}
</style>
