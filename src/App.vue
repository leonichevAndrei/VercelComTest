<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const people = ref([]);

const fetchData = async () => {
  try {
    const response = await axios.get('/api/data');
    console.log(response.data);
    people.value = response.data;
  } catch (error) {
    console.error("There was an error fetching the data!", error);
  }
};

onMounted(() => {
  fetchData();
});
</script>

<template>
  <div>
    <h1>Hello, Vue 3!</h1>
    <ul>
      <li v-for="person in people" :key="person.name">
        {{ person.name }} - {{ person.points }} points
      </li>
    </ul>
  </div>
</template>

<style scoped>
h1 {
  color: #42b983;
}
</style>