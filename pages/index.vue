<template>
  <div class="container">
    <div>
      <h1 style="margin-bottom:10px">Liste des différents processeur pour bureau :</h1>
      <div v-for="(processeur, index) in processeurs" :key="index">
      <li style="margin-left:20px;" v-if="processeur.post_title.substring(0,3) == 'Cor'"><NuxtLink :to="`processeur/${index}`" class="link"><span class="bluetext">Intel</span> {{processeur.post_title}}</NuxtLink></li>
      <li style="margin-left:20px;" v-else><NuxtLink :to="`processeur/${index}`" class="link"><span class="redtext">AMD</span> {{processeur.post_title}}</NuxtLink></li>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'homepage',
  data(){
    return {
      processeurs: [],
    }
  },
  mounted(){
    axios.get("http://wordpress-s4.local//wp-json/wp/v2/processeur").then(response =>{
      this.processeurs = response.data;
    });
  }
}

</script>

<style>
.link{
  color : black;
  text-decoration: none;
}

.redtext, .redtext:visited{
  color : red;
  font-weight: 700;
}

.bluetext, .bluetext:visited{
  color : blue;
  font-weight: 700;
}

li{
  list-style: url(https://www.flaticon.com/svg/vstatic/svg/149/149657.svg?token=exp=1614590772~hmac=2b8ac068bcf8ab30b618e0244302b921) ;
}
</style>
