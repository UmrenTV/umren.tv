<template>
  <div class="test">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "TestComponent",
  props: {
    msg: String,
  },
};
</script>

<style scoped>
</style>
