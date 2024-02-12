<script>
    export default {
        name:'FilterSelect'
    }
</script>

<template>

        <select name="type" id="type">
          <option value="" selected>All</option>
          <option value="alien">Alien</option>
          <option value="infernoble_arms">Infernoble Arms</option>
          <option value="melodious">Melodious</option>
          <option value="noble_knight">Noble Knight</option>
          <option value="archfiend">Archfiend</option>
        </select>
    
</template>


<style scoped>
#type{
    margin: 2rem 0 2rem 6%;
    padding: .5rem;
    background: var(--yu-gi-oh-white);
    border: 1px solid lightgray;
    border-radius: 5px;
    color: var(--yu-gi-oh-dark);
}
</style>