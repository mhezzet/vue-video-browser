<template>
  <div>
    <input @input="onInputChange">
  </div>
</template>

<script>
function onInputChange(event) {
  this.$emit('termChange', event.target.value)
}

export default {
  name: 'SearchBar',
  methods: {
    onInputChange
  }
}
</script>


<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>


