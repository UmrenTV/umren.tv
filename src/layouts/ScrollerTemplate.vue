<template>
  <slot></slot>
  <div class="nav">
    <scroller :sections="sections" :current="currentSection"></scroller>
  </div>
  <Footer />
  <div class="filler"></div>
</template>

<script>
import useScroller from "@/components/header/useScroller";
import Scroller from "@/components/header/Scroller";
import Footer from "@/components/footer/Footer";
export default {
  setup() {
    const sections = [
      { id: "one", mobile: "1", desktop: "Welcome" },
      { id: "two", mobile: "2", desktop: "Projects" },
      { id: "three", mobile: "3", desktop: "Experience" },
      { id: "four", mobile: "4", desktop: "Portfolio" },
      { id: "five", mobile: "5", desktop: "Hire Me" },
    ];
    const { currentSection } = useScroller(sections);
    return { currentSection, sections };
  },
  components: { Scroller, Footer },
};
</script>


<style lang="scss">
.nav {
  position: fixed;
  width: 100vw;
  height: 7vh;
  bottom: 0;
}
.filler {
  height: 7vh;
}
</style>
