<script>
    export default {
        name:'Loader'
    }
</script>

<template>

    <div  class="loader"></div>


</template>



<style scoped>


.loader{
    margin: 5rem auto;
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

</style>