<template>
    <h1>{{title}}</h1>
</template>

<script>


export default {
    name: 'Header',
    props: {
        title: String,
    },
    components: {
        
    }
}
</script>

<style>
h1 {
    text-align: center;
}


</style>