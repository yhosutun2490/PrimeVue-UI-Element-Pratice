<script setup>
import FetchAPI from '../components/Fetch-API.vue';
import {ref} from "vue"
// import { useFetch } from "@vueuse/core";
const url = "https://api.thecatapi.com/v1/images/search";
defineProps({
  msg: {
    type: String,
    required: true
  }
})
const input = ref("")
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
    <input type="text" name="" id="" v-model.lazy="input">
    <FetchAPI :url="url" #="{res:response, loading}" :watchValue="input">
      <h3>貓貓圖</h3>
      <div v-if="loading">
        <h1>...isLoading</h1>
      </div>
      <div v-if="response && response[0]">
        <img :src="response[0].url" alt="" srcset="" class="cat-img"/>
      </div>
    </FetchAPI>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
.cat-img {
  widows: 400px;
  height: 300px;
}
</style>
