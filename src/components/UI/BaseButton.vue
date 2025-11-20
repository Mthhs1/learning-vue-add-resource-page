<template>
    <button :class="mode">
        <slot></slot>
    </button>
</template>

<script>
export default {
    props: ['mode']
}
</script>

<style scoped>


button {

    font-family: inherit;
    background-color: transparent;
    color: white;
    border: none;
    background-color: rgb(54, 0, 54);
    
    height: 2.5rem;
    width: 6rem;

    box-shadow: 0 0 5px 1px rgba(0, 0, 0, 0.09);

}

button:hover {
    background-color: rgb(99, 0, 99);
}

.flat {


    border: solid;
    border: none;
    background-color: transparent;
    color: purple;

}

.flat:hover {

    background-color: rgba(128, 0, 128, 0.219);
    color: purple;

}
</style>