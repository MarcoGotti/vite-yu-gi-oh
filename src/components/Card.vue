<script>
    export default {
        name:'Card',
        props:{
            card: Object
        }
    }
</script>

<template>
    
    <div  class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl" >
        <div class="card">
            <img :src="card.card_images[0].image_url_small" alt="">
            <h4 class="name">
                {{ card.name }}
            </h4>
            <div class="archetype">
                {{ card.archetype }}
            </div>
            <div class="type">
                {{ card.type }}
            </div>
            <div class="race">
                {{ card.race }}
            </div>
            <div class="attribute">
                {{ card.attribute }}
            </div>
        
        </div>
    </div>

</template>



<style scoped>
.card:hover img{
    scale: 1.03;
    filter: drop-shadow(0 0 15px var(--yu-gi-oh-primary));
}
.card{
  height: 100%;
  text-align: center;
  background-color: var(--yu-gi-oh-primary);
  padding-bottom: .25rem;
  transition: all 0.3s;

  > img {
    width: 100%;
    display: block;
    transition: all .5s;
  }

  > .name{
    text-transform: uppercase;
    color: var(--yu-gi-oh-white);
    padding: 1rem .5rem;
  }

  > .archetype{
  }
  > .type{
    color: var(--yu-gi-oh-type);
  }
  > .race{
    color: var(--yu-gi-oh-race);
  }
  > .attribute{
    color: var(--yu-gi-oh-attribute);
  }
}
</style>