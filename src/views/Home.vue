<template>
  <div class="home">
    <TestComponent msg="Test Component" />
  </div>
</template>

<script>
// @ is an alias to /src
import TestComponent from "@/components/TestComponent.vue";

export default {
  name: "Home",
  components: {
    TestComponent,
  },
};
</script>

<style lang="scss">
.section {
  height: 100vh;
}
</style>
