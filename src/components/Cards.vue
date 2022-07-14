<template>

</template>

<script>
export default {
  name: 'Card',
  data() {
    return {

      toggle: false,
      show2: 'show2',
      unshow2: 'unshow2',
    }
  },

  methods: {
    appear() {
      this.toggle = !this.toggle
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
