<template>
  <div id="scroller">
    <p
      v-for="s in sectionsProps"
      :key="s"
      class="link"
      :class="currentSection === s ? 'active' : ''"
      @click="changeSection(s)"
    >
      {{ s }}
    </p>
  </div>
</template>

<script>
import { ref, watch } from "vue";
export default {
  props: {
    sections: { type: Array, default: () => [] },
    current: { type: String, default: "" },
  },
  setup(props) {
    const currentSection = ref(props.sections[0]);
    const changeSection = (section) => {
      document.getElementById(section).scrollIntoView({ behavior: "smooth" });
    };
    watch(props, (val) => {
      currentSection.value = val.current;
    });

    return {
      changeSection,
      currentSection,
      sectionsProps: props.sections,
      currentProp: props.current,
    };
  },
};
</script>

<style lang="scss">
#scroller {
  border-radius: 0.8vw;
  position: fixed;
  width: 7vw;
  top: 3%;
  right: 2%;
  background-color: rgba(0, 0, 0, 0.75);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.link {
  text-transform: capitalize;
  cursor: pointer;
  color: white;
  transition: 0.3s ease-in-out;
  font-size: 1.3vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 3vw;
}
// .link:first-child {
//   padding-top: 0.5vw;
// }
// .link:last-child {
//   padding-bottom: 0.5vw;
// }
.link:hover {
  font-size: 1.5vw;
}

.active {
  color: rgb(0, 100, 255);
  font-size: 1.5vw;
}
</style>
