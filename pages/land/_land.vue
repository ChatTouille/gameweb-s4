<template>
    <div>
        <h1>{{fr}} / {{land.nativeName}}</h1>
        <ul>
            <li>Population : {{land.population}} habitants</li>
            <li>Capitale : {{land.capital}}</li>
        </ul>
        <img :src="land.flag" />
        
    </div>
</template>
<script>
import axios from 'axios';
export default {
    data(){
        return{
            land:[],
            fr:[],
        }
    },
    mounted(){
        let nbr = this.$route.params.land;
        axios.get("https://restcountries.eu/rest/v2/all").then(response => {
            this.land = response.data[nbr];
            //console.log(nbr)
            this.fr = this.land.translations.fr;
        });
    }
}
</script>