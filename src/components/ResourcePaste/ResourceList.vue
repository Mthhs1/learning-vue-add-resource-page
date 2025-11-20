<template>
    <ul>
        <resource-item v-for="obj in resourceList" :key="obj.id" :resourceObject="obj"></resource-item>
    </ul>
</template>

<script>

import ResourceItem from './ResourceItem.vue'

export default {

    components: {
        ResourceItem,
    },

    props: ['resourceList']
}
</script>

<style scoped>
    ul {
        margin: 0;
        padding: 0;
        
        display: flex;
        flex-direction: column;
        align-items: center;
        /* justify-content: center; */
    }
</style>