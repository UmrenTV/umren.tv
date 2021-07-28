<template>
  <div>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <scroller
      :sections="sections"
      :current="currentSection"
      @changed="scrollToSection"
    ></scroller>
    <router-view />
    <div id="one">One</div>
    <div id="two">Two</div>
    <div id="three">Three</div>
    <div id="four">Four</div>
    <div id="five">Five</div>
  </div>
</template>
<script>
import useScroller from "@/components/header/useScroller";
import Scroller from "@/components/header/Scroller";
export default {
  setup() {
    const sections = ["one", "two", "three", "four", "five"];
    const { currentSection, scrollToSection } = useScroller(sections);
    return { scrollToSection, currentSection, sections };
  },
  components: { Scroller },
};
</script>
<style>
#one,
#two,
#three,
#four,
#five {
  border-top: 1px solid black;
  height: 100vh;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
