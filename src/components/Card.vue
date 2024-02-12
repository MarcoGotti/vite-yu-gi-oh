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
        
        </div>
    </div>

</template>



<style scoped>
.card{
  height: 100%;
  text-align: center;
  background-color: var(--yu-gi-oh-primary);
  padding-bottom: .25rem;

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
  }
}
</style>