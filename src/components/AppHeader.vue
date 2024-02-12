<template>

    <header>

        <img src="https://tse2.mm.bing.net/th?id=OIP.bUBYysYCfLWFWYpfQ8i8KAHaCh&pid=Api" alt="">
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
        width: 80px;
        
    }

    > p{
        font-size: 50px;
    }
}

</style>