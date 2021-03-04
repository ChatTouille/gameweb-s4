<template>
    <div>
        <div class="container">
        <h1>{{marque}} {{processeur.post_title}}</h1>
        <h2 style="margin-top:20px;">Détails :</h2>
        <ul><li>Coeurs / Threads : {{coeurs}} / {{threads}}</li>
        <li>Finesse de gravure : {{gravure}} nm</li>
        </ul>
        <button style="margin-top:20px;">>> En savoir plus sur le processeur d'{{marque}}</button>
        <p style="margin-top:10px;"><a href="../">Revenir sur la page des processeurs</a></p>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    data(){
        return{
            processeur:[],
            marque:[],
            coeurs:[],
            threads:[],
            gravure:[],
        }
    },
    mounted(){
        let nbr = this.$route.params.processeur;
        axios.get("http://wordpress-s4.local//wp-json/wp/v2/processeur").then(response => {
            this.processeur = response.data[nbr];
            //console.log(nbr)
            this.marque = this.processeur.acf.marque;
            this.coeurs = this.processeur.acf.coeurs;
            this.threads = this.processeur.acf.nombre_de_threads;
            this.gravure = this.processeur.acf.finesse_de_gravure_en_nanometres;
        });
    }
}
</script>

<style>
    .container{
        width: 500px;
        margin: auto;
        text-align : center;
    }
</style>