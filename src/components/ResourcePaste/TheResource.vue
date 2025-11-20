<template>
    <div class="div-container-resource">
        <base-card class="buttons">
            <base-button @click="setTab('resource-list')" :mode="atualTab === 'resource-list' ? 'flat' : ''">
                Stored Resources</base-button>
            <base-button @click="setTab('add-new-resource')" :mode="atualTab === 'add-new-resource' ? 'flat' : ''">
                Add new Resource</base-button>
        </base-card>
    </div>
    <keep-alive>
        <component :is="atualTab" v-bind="atualProps" v-on="componentEvents"></component>
    </keep-alive>
</template>

<script>

import AddNewResource from "./AddNewResource.vue";
import ResourceList from "./ResourceList.vue"


export default {

    components: {
        ResourceList,
        AddNewResource
    },

    data() {
        return {
            atualTab: "resource-list",
            staticId: 2,
            storedResources: [
                {
                    id: 1,
                    title: "Vue Oficial Guide",
                    description: "The Vue oficial guide to Learn About the framkework",
                    link: "https://vuejs.org/"
                },
                {
                    id: 2,
                    title: "Google",
                    description: "Learn to google...",
                    link: "https://google.com",
                },
            ],
        }
    },

    methods: {

        getId() {
            this.staticId++
            return this.staticId
        },

        setTab(tab) {
            this.atualTab = tab
        },

        setNewResource(title, description, link) {

            const id = this.getId()
            const objeto = { id: id, title: title, description: description, link: link, }
            this.storedResources.push(objeto)
            console.log(objeto)
            this.atualTab = "resource-list"

        },

        removeResource(id) {
            this.storedResources = this.storedResources.filter(obj => obj.id !== id)
        }
    },

    computed: {

        componentEvents() { return { 'send-new-resource': this.setNewResource } },

        atualProps() {
            if (this.atualTab === 'resource-list') {
                return { resourceList: this.storedResources }
            } else {
                return {}
            }

        }

    },

    provide() {
        return {
            removeResource: this.removeResource,
        }
    },

}
</script>

<style scoped>
.div-container-resource {
    display: flex;
    justify-content: center;
}

.buttons {

    display: flex;
    flex-direction: row;

    align-items: center;
    justify-content: flex-start;

    width: 30%;

}
</style>