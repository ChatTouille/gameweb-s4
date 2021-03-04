<template>
  <div class="container">
    <div>
      <li v-for="(land, index) in lands" :key="index"><NuxtLink :to="`land/${index}`">{{land.name}}</NuxtLink></li>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'homepage',
  data(){
    return {
      lands: [],
    }
  },
  mounted(){
    axios.get("https://restcountries.eu/rest/v2/all").then(response => this.lands = response.data);
  }
}

</script>

<style>

</style>
