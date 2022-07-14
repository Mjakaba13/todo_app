<template>

</template>

<script>
export default {
    name: 'Input',
    data() {
        return {

            toggle: false,
            show2: 'show2',
            unshow2: 'unshow2',
            text: "",
            List: {}
        }
    },

    methods: {
        appear() {
            this.toggle = !this.toggle
        },
        pusher() {
            this.List.push(this.text)
        }

    }

}
</script>
<style scoped>
</style>