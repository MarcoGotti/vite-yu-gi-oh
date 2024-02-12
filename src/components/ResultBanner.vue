<script>
    export default {
        name:'ResultBanner',
        props:{
            result: Number
        }
    }
</script>

<template>
    
    <div class="result">
        <strong>Found {{ result }} cards</strong>
    </div>

</template>


<style scoped>
.result{
    background-color: var(--yu-gi-oh-dark);
    color: var(--yu-gi-oh-white);
    padding: 1.75rem;
    font-size: larger;
}
</style>