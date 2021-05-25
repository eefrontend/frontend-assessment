<template>
  <tabs-display
    :data="data"
    :activeKey="activeKey"
    :onChangeActiveKey="handleChangeActiveKey"
  />
</template>

<script>
import TabsDisplay from "./TabsDisplay.vue";

export default {
  components: { TabsDisplay },
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
      this.activeKey = key;
    },
  },
};
</script>

<style scoped></style>
