<template>
  <div id="scroller">
    <div
      v-for="s in sectionsProps"
      :key="s.id"
      class="links-container"
      @click="changeSection(s)"
      :class="[currentSection === s.id ? 'active' : '', deviceType]"
      :style="linksStyles(s.id)"
    >
      <div class="mobile-container" v-if="deviceType === 'mobile'">
        <div
          class="link mobile unselectable"
          :class="currentSection === s.id ? 'active' : ''"
        >
          {{ s.mobile }}
        </div>
        <transition name="span">
          <div
            class="links-span unselectable"
            :class="currentSection === s.id ? 'active' : ''"
            :style="spanStyles(s.id)"
          >
            {{ s.desktop }}
          </div></transition
        >
      </div>
      <div
        class="link desktop unselectable"
        v-else
        :class="currentSection === s.id ? 'active' : ''"
      >
        {{ s.desktop }}
      </div>
    </div>
  </div>
</template>

<script>
import { ref, watch, onMounted, onUnmounted } from "vue";
export default {
  props: {
    sections: { type: Array, default: () => [] },
    current: { type: String, default: "" },
  },
  setup(props) {
    const currentSection = ref(props.sections[0]);
    const deviceType = ref("");
    const sectionProps = [
      ...props.sections,
      { id: "footer", mobile: "F", desktop: "Footer" },
    ];
    const changeSection = (section) => {
      document
        .getElementById(section.id)
        .scrollIntoView({ behavior: "smooth" });
    };
    const checkViewport = () => {
      if (window.innerWidth <= 812) {
        deviceType.value = "mobile";
      } else {
        deviceType.value = "desktop";
      }
    };

    // const currentActive = (id) => {
    //   if (currentSection.value === id) {
    //     setTimeout(() => {
    //       return true;
    //     }, 100);
    //   }
    // };

    const widthCalculated = ref(null);
    const activeWidth = 35;

    const linksStyles = (id) => {
      if (deviceType.value === "mobile") {
        if (currentSection.value === id) {
          return `width: ${activeWidth}vw`;
        } else {
          widthCalculated.value =
            (100 - activeWidth) / (sectionProps.length - 1);
          return `width: ${widthCalculated.value}vw`;
        }
      } else {
        widthCalculated.value = 100 / (sectionProps.length - 1);
        return `width: ${widthCalculated.value}vw`;
      }
    };
    const spanStyles = (id) => {
      if (currentSection.value === id && widthCalculated && activeWidth) {
        return `width: ${activeWidth - widthCalculated.value}vw`;
      } else {
        return "width: 0px";
      }
    };
    onMounted(() => {
      window.addEventListener("resize", checkViewport);
      checkViewport();
    });
    onUnmounted(() => {
      window.removeEventListener("resize", checkViewport);
    });

    watch(props, (val) => {
      currentSection.value = val.current;
    });

    return {
      deviceType,
      spanStyles,
      changeSection,
      currentSection,
      linksStyles,
      // currentActive,
      sectionsProps: sectionProps,
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
.mobile-container {
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: center;
}
.unselectable {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.links-container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  // flex: 1;
  cursor: pointer;
  transition: 0.1s ease-in-out;
  &.active {
    background: rgba(0, 0, 0, 0.85);
  }
  &.mobile {
    transition: 0.1s ease-in-out;
    &.active {
      //  flex: 3;
      background: rgba(0, 0, 0, 0.9);
    }
  }
}
.links-container:hover {
  background: rgba(0, 0, 0, 0.85);
}
.links-span {
  opacity: 0;
  font-size: 0;
  padding: 0;
  width: 0px;
  transition: 0.05s ease-in-out;
  &.active {
    opacity: 1;
    padding-left: 2vw;
    font-size: 3.5vw;
    transition: 0.1s 0.1s ease-in-out;
  }
}
.span-enter-active {
  transition: 0.1s ease-in-out;
  transition-delay: 0.3s;
}
.span-leave-active {
  transition: 0s ease-in-out;
  transition-delay: 0.05s;
}
.span-enter-from {
  opacity: 0;
  width: 0px;
}
.span-enter-to {
  opacity: 1;
}
.span-leave-to {
  opacity: 0;
  width: 0px;
}

.link {
  color: white;
  transition: 0.1s ease-in-out;
  font-size: 1vw;
  &.mobile {
    @media screen and (max-width: 812px) {
      font-size: 3.5vw;
    }
  }
  &.desktop {
    font-size: 1.8vw;
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
    // font-size: 1.8vw;
    &.mobile {
      // font-size: 5vw;
    }
  }
}

.active {
  color: var(--color-primary);
  &.desktop {
    //font-size: 1.8vw;
  }
  &.mobile {
    // font-size: 5vw;
  }
}
</style>
