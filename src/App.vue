<script>
import axios from 'axios';
import AppHeader from "./components/AppHeader.vue";
import AppFooter from "./components/AppFooter.vue";

export default {
  name:'App',
  components:{
    AppHeader,
    AppFooter
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
      console.log(response.data.data);
      this.cards = response.data.data
      console.log(this.cards);
      console.log(this.cards[0].card_images[0].image_url_small)
    })
    .catch((error) => {
      this.error = error.message;
      console.log(error);
    })

  }

}

</script>

<template>

  <AppHeader></AppHeader>
 
 <main>

  <div class="container">
    <div class="row">
      <div v-for="card in cards" class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl">
        <div class="card">
          <img :src="card.card_images[0].image_url_small" alt="">
          <h4 class="name">
            {{ card.name }}
          </h4>
          <div class="archetype">
            {{ card.archetype }}
          </div>
          
        </div>
      </div>
    </div>
  </div>



 </main>

 <AppFooter></AppFooter>
 
</template>

<style>

.card{
  height: 100%;
  text-align: center;
  background-color: var(--yu-gi-oh-primary);

  > img {
    width: 100%;
    display: block;
  }

  > .name{
    text-transform: uppercase;
    color: var(--yu-gi-oh-white);
    padding: 1rem .5rem;
  }

  > .archetype{
    color: var(--yu-gi-oh-dark);
  }
}

</style>
