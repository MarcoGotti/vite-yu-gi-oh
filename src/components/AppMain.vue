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
            main_api_url:'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0',
            cards: [],
            filtered_cards:[],
            cards_archetypes:[],
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
                this.cards.forEach(card => {
                    if (card.archetype && !this.cards_archetypes.includes(card.archetype)){
                        this.cards_archetypes.push(card.archetype)
                    }
                }); 
                console.log(this.cards_archetypes);
                console.log(this.cards);
            })

            .catch((error) => {
                this.error = error.message;
                console.log(error);
            })
        },
        filterCards(data){

            const [selectedOption] = data;
            console.log(selectedOption);

            return selectedOption === '' ? console.log(this.cards) : console.log(this.cards.filter(card => card.archetype === selectedOption));
        }
    },
    created(){
        this.getCards(this.main_api_url)       
    }
}
</script>

<template>

    <main>

        <FilterSelect :select_options="cards_archetypes" @filterResults="filterCards"></FilterSelect><!-- @filterResults="filterCards" -->
        <Loader v-if="loader"></Loader>
        
        <section v-else id="wrapper">
            <div class="container">

                <ResultBanner :result="getResult"></ResultBanner>

                <div class="row">

                    <Card
                        
                        :cards="cards">
                    </Card>
                    <!-- v-for="card in cards"
                        :key="card.id + '_' + card.name" -->
                    
                </div>
            </div>
        </section>

    </main>

</template>



<style scoped>

</style>