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
            main_api_url:'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=300&offset=0',
            cards: [],
            error: false
        }
    },
    mounted(){
        axios
        .get(this.main_api_url)
        .then((response) => {
            console.log(response);
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
        <div v-if="cards.length == 0" class="loader"></div>
        <section v-else id="wrapper">



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

.loader{
    margin: auto;
    border: 8px solid var(--yu-gi-oh-dark);
    border-radius: 50%;
    border-top: 8px solid var(--yu-gi-oh-primary);
    width: 100px;
    height: 100px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
.result{
    background-color: var(--yu-gi-oh-dark);
    color: var(--yu-gi-oh-white);
    padding: 1.75rem;
    font-size: larger;
}
</style>