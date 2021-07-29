<template>
  <scroller-template>
    <div class="home">
      <div class="content">
        <div class="section" id="one"><h1>One</h1></div>
        <div class="section" id="two"><h1>Two</h1></div>
        <div class="section" id="three"><h1>Three</h1></div>
        <div class="section" id="four"><h1>Four</h1></div>
        <div class="section" id="five"><h1>Five</h1></div>
      </div>
    </div>
  </scroller-template>
</template>

<script>
import ScrollerTemplate from "@/layouts/ScrollerTemplate";
export default {
  name: "Home",
  setup() {},
  components: {
    ScrollerTemplate,
  },
};
</script>

<style lang="scss">
#one,
#two,
#three,
#four,
#five {
  padding-top: 15px;
  border-top: 1px dotted rgba(0, 0, 0, 0.2);
  height: 93vh;
  h1 {
    font-size: 45px;
  }
}
.content {
}
</style>
