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
  setup(props, { emit }) {
    const currentSection = ref(props.sections[0]);
    const changeSection = (section) => {
      currentSection.value = section;
      emit("changed", section);
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
  border-radius: 9px;
  position: fixed;
  top: 3%;
  right: 2%;
  background-color: rgba(0, 0, 0, 0.75);
}
.link {
  padding: 12px 20px;
  text-transform: capitalize;
  cursor: pointer;
  color: white;
  transition: 0.3s ease-in-out;
  font-size: 15px;
}
.link:first-child {
  padding-top: 24px;
}
.link:last-child {
  padding-bottom: 24px;
}
.link:hover {
  color: orange;
}

.active {
  color: rgb(0, 100, 255);
}
</style>
