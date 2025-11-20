<template>
    <base-dialog v-if="inputUserIsEmpty" title="Empty Input" v-on:close="confirmError">
        <template #default>
            <p>Unfortunely, at least one input value is invalid.</p>
            <p>Check all inputs and try again.</p>
        </template>
        <template #action>
            <base-button @click="confirmError">Ok</base-button>
        </template>
    </base-dialog>
    <div class="div-container-new-resource">
        <base-card class="card-new-resource">

            <form v-on:submit.prevent="sendNewResource" class="form-container-new-resource">

                <div class="form-div container">
                    <p>Title</p>
                    <input type="text" ref="user_input_title">
                </div>
                <div class="form-div">
                    <p>Description</p>
                    <textarea type="text" rows="3" ref="user_input_description"></textarea>
                </div>
                <div class="form-div">
                    <p>Link</p>
                    <input type="text" ref="user_input_link">
                </div>
                <base-button>Add Resource</base-button>

            </form>
        </base-card>
    </div>
</template>

<script>
export default {

    data() {
        return {
            inputUserIsEmpty: false
        }
    },

    emits: ["send-new-resource"],



    methods: {
        sendNewResource() {
            const user_input_title = this.$refs.user_input_title.value
            const user_input_description = this.$refs.user_input_description.value
            const user_input_link = this.$refs.user_input_link.value

            if (user_input_title.trim() === "" || user_input_description.trim() === "" || user_input_link.trim() === "") {

                this.inputUserIsEmpty = true
                return
            }

            this.$emit("send-new-resource", user_input_title, user_input_description, user_input_link)

            this.$refs.user_input_title.value = ""
            this.$refs.user_input_description.value = ""
            this.$refs.user_input_link.value = ""

        },

        confirmError () {
            this.inputUserIsEmpty = false
        }
    }
}
</script>

<style scoped>
p {
    margin: 0;
    font-weight: bold;
}

.div-container-new-resource {
    display: flex;
    justify-content: center;
}

.card-new-resource {
    width: 40rem;
}

.form-container-new-resource {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;

    justify-content: center;
    align-items: center;
}

.form-div {
    width: 95%;
}

input,
textarea {
    resize: vertical;
    width: 100%;
}
</style>
