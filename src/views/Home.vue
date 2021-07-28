<template>
  <div class="home">
    <scroller
      :sections="sections"
      :current="currentSection"
      @changed="scrollToSection"
    ></scroller>
    <div class="section" id="one"><h1>One</h1></div>
    <div class="section" id="two"><h1>Two</h1></div>
    <div class="section" id="three"><h1>Three</h1></div>
    <div class="section" id="four"><h1>Four</h1></div>
    <div class="section" id="five"><h1>Five</h1></div>
  </div>
</template>

<script>
import useScroller from "@/components/header/useScroller";
import Scroller from "@/components/header/Scroller";
export default {
  name: "Home",
  setup() {
    const sections = ["one", "two", "three", "four", "five"];
    const { currentSection, scrollToSection } = useScroller(sections);
    return { scrollToSection, currentSection, sections };
  },
  components: { Scroller },
};
</script>

<style lang="scss">
#one,
#two,
#three,
#four,
#five {
  border-top: 1px dotted rgba(0, 0, 0, 0.2);
  height: 100vh;
}
</style>
