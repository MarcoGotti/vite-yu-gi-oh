<script>

import axios from 'axios';
import Card from "./Card.vue";
import FilterSelect from "./FilterSelect.vue";

export default {
    name:'AppMain',
    components:{
        Card,
        FilterSelect
    },
    data(){
        return{
            main_api_url:'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
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

        <FilterSelect></FilterSelect>

        <section id="wrapper">

            <div class="container">

                <div class="result">
                    <strong>Found {{ cards.length }} cards</strong>
                </div>

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
.result{
    background-color: var(--yu-gi-oh-dark);
    color: var(--yu-gi-oh-white);
    padding: 1.75rem;
    font-size: larger;
}
</style>