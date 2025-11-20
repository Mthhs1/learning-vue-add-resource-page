<template>
    <li>
        <base-card class="container">
            <header class="resourceItem__header">
                <h3>{{ resourceObject.title }}</h3>
                <base-button mode="flat" @click="removeResource(resourceObject.id)">Delete</base-button>
            </header>
            <main class="resourceItem__main">
                <p>{{ resourceObject.description }}</p>
                <a :href=resourceObject.link target="blank"> View Resource </a>
            </main>
        </base-card>
    </li>
</template>

<script>
export default {
    props: ['resourceObject'],
    methods: {

    },

    inject: ['removeResource']
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Geist+Mono:wght@100..900&family=Roboto:ital,wght@0,100..900;1,100..900&family=SUSE+Mono:ital,wght@0,100..800;1,100..800&family=Sansation:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&display=swap');

.container {
    display: flex;
    flex-direction: column;
}

li {
    list-style: none;
    width: 40rem;
}

header {
    display: flex;

    justify-content: space-between;
    align-items: center;
}

.resourceItem__header h3 {
    font-size: 1.5rem;
    margin: .5rem 0;
}

.resourceItem__main a {

    text-decoration: none;
    color: orange;
    font-size: 1rem;
}

.resourceItem__main p {
    margin: 0.5rem 0;
    font-size: 1rem;
}


</style>
