<template>
  <div class="responsive-data-display">
    <tabs-display
      class="tabs-display"
      :data="data"
      :activeKey="activeKey"
      :onChangeActiveKey="handleChangeActiveTabKey"
    />

    <accordion-display
      class="accordion-display"
      :data="data"
      :activeKey="activeKey"
      :onChangeActiveKey="handleChangeActivePanelKey"
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
    handleChangeActivePanelKey(key) {
      if (key === this.activeKey) {
        this.activeKey = null;
        return;
      }

      this.activeKey = key;
    },
    handleChangeActiveTabKey(key) {
      this.activeKey = key;
    },
  },
};
</script>

<style lang="scss" scoped>
.responsive-data-display {
  box-shadow: $box-shadow-1;
}

.accordion-display {
  display: none;
}

@media screen and (max-width: $media-phone) {
  .accordion-display {
    display: block;
  }

  .tabs-display {
    display: none;
  }
}
</style>
