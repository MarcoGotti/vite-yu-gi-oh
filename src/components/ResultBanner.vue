<script>
    export default {
        name:'ResultBanner',
        props:{
            result: String
        }
    }
</script>

<template>
    
    <div class="result">
        <strong>{{ result }}</strong>
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