<script setup>
import { ref, reactive } from "vue";

// ref for primitives (number, string, etc)
let count = ref(0);

// reactive for objects
let courses = reactive([
  {
    title: "Javascript",
  },
  {
    title: "React",
  },
  {
    title: "Vue",
  },
]);

let newCourse = reactive({});

// .value for ref()
function increment() {
  count.value++;
}

function addCourse() {
  courses.push(newCourse);
  newCourse = {};
}
</script>

<template>
  <div>
    <h1>Courses List</h1>
    <ul>
      <li v-for="course in courses" :key="course.title">
        {{ course.title }}
      </li>
    </ul>
    <br />
    <input v-model="newCourse.title" type="text" />
    <button @click="addCourse">Add</button>
  </div>
</template>

<style scoped></style>
