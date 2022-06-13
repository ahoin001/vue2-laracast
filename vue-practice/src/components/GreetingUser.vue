<template class="center-text">
  <h1>Welcome Back to Hero List {{name}} !</h1>
</template>

<script>
export default {
  name: "GreetingUser",
  props:{
          name: {
            type: String,
            default: ', whoops, forgot my name!',
            required: true,
          }
  }
}
</script>

<style scoped>
  .center-text {
    text-align: center;
  }
</style>