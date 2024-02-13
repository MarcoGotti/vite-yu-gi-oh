<script>

import axios from 'axios';
import Card from "./Card.vue";
import FilterSelect from "./FilterSelect.vue";
import Loader from "./Loader.vue";
import ResultBanner from "./ResultBanner.vue";

export default {
    name:'AppMain',
    components:{
        Card,
        FilterSelect,
        Loader,
        ResultBanner
    },
    data(){
        return{
            main_api_url:'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=100&offset=0',
            cards: [],
            loader: true,
            error: false
        }
    },
    computed:{
        getResult(){
            return this.cards ? 'Found ' + this.cards.length + ' results' : '0 results'
        }
    },
    methods:{
        getCards(url){
            axios
            .get(url)
            .then((response) => {
           
                this.cards = response.data.data;  
                this.loader = false;   
            })

            .catch((error) => {
                this.error = error.message;
                console.log(error);
            })
        }
    },
    created(){
        this.getCards(this.main_api_url)
        
    }
}
</script>

<template>

    <main>

        <FilterSelect ></FilterSelect>
        <Loader v-if="loader"></Loader>
        
        <section v-else id="wrapper">
            <div class="container">

                <ResultBanner :result="getResult"></ResultBanner>

                <div class="row">

                    <Card
                        v-for="card in cards"
                        :key="card.id + '_' + card.name"
                        :card="card">
                    </Card>
                    
                </div>
            </div>
        </section>

    </main>

</template>



<style scoped>

</style>