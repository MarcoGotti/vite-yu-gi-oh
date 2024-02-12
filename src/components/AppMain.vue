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
            main_api_url:'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=300&offset=0',
            cards: [],
            error: false
        }
    },
    mounted(){
        axios
        .get(this.main_api_url)
        .then((response) => {
           
            this.cards = response.data.data;     
        })

        .catch((error) => {
            this.error = error.message;
            console.log(error);
        })
    }
}
</script>

<template>

    <main>

        <FilterSelect ></FilterSelect>
        <Loader v-if="cards.length == 0"></Loader>
        
        <section v-else id="wrapper">
            <div class="container">

                <ResultBanner :result="cards.length"></ResultBanner>

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