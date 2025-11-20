<template>
    <header>{{ title }}</header>
</template>

<script>

export default {
    props: ['title']
}
</script>

<style scoped>
header {
    width: 100%;
    height: 15vh;

    margin-bottom: 1.3rem;

    text-align: center;
    align-content: center;

    font-size: 2rem;
    font-weight: bold;

    color: white;
    background-color: darkred;
}
</style>