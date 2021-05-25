<template>
  <div class="accordion-display">
    <div>
      <div
        v-for="(item, index) in data"
        :key="index"
        @click="onChangeActiveKey(index)"
      >
        <div
          :class="[
            'accordion-display__panel',
            { 'accordion-display__panel--active': activeKey === index },
          ]"
        >
          {{ item.title }}
        </div>

        <div
          v-if="activeKey !== null"
          class="accordion-display__content"
          v-html="item.content"
          v-show="activeKey === index"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: Array,
    activeKey: Number,
    onChangeActiveKey: Function,
  },
};
</script>

<style scoped>
.accordion-display__panel {
  height: 4rem;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 1.5rem;
  font-size: 1rem;
  background-color: #c8e6c9;
  cursor: pointer;
  position: relative;
  transition-property: background-color;
  transition-duration: 150ms;
}

.accordion-display__panel:hover {
  background-color: #a5d6a7;
}

.accordion-display__panel--active {
  background-color: #4caf50;
  color: #ffffff;
}

.accordion-display__panel--active:hover {
  background-color: #4caf50;
}

.accordion-display__content {
  background-color: #f5f5f5;
  padding: 1.5rem;
  line-height: 200%;
}
</style>
