<template>
  <div id="app">
    <h1>Welcome to the Fun Zone! 😄</h1>
    <button @click="getJoke">Tell me a joke!</button>
    <p v-if="joke">{{ joke }}</p>
  </div>
</template>

<script>
import axios from 'axios';
import {developmentServerURL as url}  from '@/constants.js';

export default {
  data() {
    return {
      joke: '',
    };
  },
  methods: {
    async getJoke() {
      try {
        const response = await axios.get(url + 'joke');
        this.joke = response.data.joke;
      } catch (error) {
        this.joke = 'Oops! No jokes today. 🤷‍♂️';
      }
    },
  },
};
</script>

<style scoped>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.h1 {
  color: #333;
}
p {
  color: #666;
}

button {
  padding: 10px 20px;
  background-color: #333;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #555;
}



</style>
