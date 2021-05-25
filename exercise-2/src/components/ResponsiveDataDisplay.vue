<template>
  <div>
    <tabs-display
      class="tabs-display"
      :data="data"
      :activeKey="activeKey"
      :onChangeActiveKey="handleChangeActiveKey"
    />

    <accordion-display
      class="accordion-display"
      :data="data"
      :activeKey="activeKey"
      :onChangeActiveKey="handleChangeActiveKey"
    />
  </div>
</template>

<script>
import AccordionDisplay from "./AccordionDisplay.vue";
import TabsDisplay from "./TabsDisplay.vue";

export default {
  components: { TabsDisplay, AccordionDisplay },
  props: {
    data: Array,
  },
  data() {
    return {
      activeKey: 0,
    };
  },
  methods: {
    handleChangeActiveKey(key) {
      if (key === this.activeKey) {
        this.activeKey = null;
        return;
      }

      this.activeKey = key;
    },
  },
};
</script>

<style scoped>
.accordion-display {
  display: none;
}
@media screen and (max-width: 600px) {
  .accordion-display {
    display: block;
  }

  .tabs-display {
    display: none;
  }
}
</style>
