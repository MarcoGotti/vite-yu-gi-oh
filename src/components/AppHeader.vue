<template>

    <header>

        <img src="https://images.ygoprodeck.com/images/assets/ygoprodeck_header_logo.png?v=1.13" alt="">
        <p>Yu-Gi-Oh Api</p>

    </header>
    
</template>

<script>
    export default {
        name:'AppHeader'
    }
</script>

<style scoped>

header{
    background-color: var(--yu-gi-oh-white);
    padding: 2rem;
    display: flex;
    align-items: center;

    > img {   
        margin-right: 2rem;
        width: 100px;
        
    }

    > p{
        font-size: 50px;
    }
}

</style>