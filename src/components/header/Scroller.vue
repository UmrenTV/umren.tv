<template>
  <div id="scroller">
    <div
      v-for="s in sectionsProps"
      :key="s.id"
      class="links-container"
      @click="changeSection(s)"
    >
      <p class="link mobile" :class="currentSection === s.id ? 'active' : ''">
        {{ s.mobile }}
      </p>
      <p class="link desktop" :class="currentSection === s.id ? 'active' : ''">
        {{ s.desktop }}
      </p>
    </div>
    <!-- <div class="scroller-mobile"> -->
    <!--     <p -->
    <!--         v-for="s in sectionsProps" -->
    <!--         :key="s" -->
    <!--         class="link" -->
    <!--         :class="currentSection === s ? 'active' : ''" -->
    <!--         @click="changeSection(s)" -->
    <!--         > -->
    <!--         {{ s.mobile }} -->
    <!--     </p> -->
    <!-- </div> -->
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
      document
        .getElementById(section.id)
        .scrollIntoView({ behavior: "smooth" });
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
  background-color: rgba(0, 0, 0, 0.75);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  height: 100%;
  width: 100%;
}
.links-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex: 1;
  cursor: pointer;
}
.link {
  color: white;
  transition: 0.2s ease-in-out;
  font-size: 1vw;
  &.mobile {
    display: none;
    @media screen and (max-width: 800px) {
      display: block;
      font-size: 3.5vw;
    }
  }
  &.desktop {
    font-size: 1.3vw;
    display: block;
    @media screen and (max-width: 800px) {
      display: none;
    }
  }
}
// .link:first-child {
//   padding-top: 0.5vw;
// }
// .link:last-child {
//   padding-bottom: 0.5vw;
// }
.links-container:hover {
  .link {
    font-size: 1.8vw;
    &.mobile {
      font-size: 5vw;
    }
  }
}

.active {
  color: rgb(0, 100, 255);
  &.desktop {
    font-size: 1.8vw;
  }
  &.mobile {
    font-size: 5vw;
  }
}
</style>
