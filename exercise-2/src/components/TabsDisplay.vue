<template>
  <div class="tabs-display">
    <div>
      <div
        v-for="(item, index) in data"
        :class="['tab', { 'tab--active': activeKey === index }]"
        :key="index"
        @click="onChangeActiveKey(index)"
      >
        {{ item.title }}

        <div class="tab__indicator" v-show="activeKey === index" />
      </div>
    </div>

    <div v-if="activeKey !== null" class="tabs-display__content">
      <h1 class="tabs-display__content-title">
        {{ data[activeKey].title }}
      </h1>

      <div
        class="tabs-display__content-html"
        v-html="data[activeKey].content"
      />
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
.tabs-display {
  display: flex;
  height: 32rem;
  background-color: #c8e6c9;
  border: 1px solid #c8e6c9;
}

.tab {
  min-width: 12rem;
  height: 4rem;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 1.5rem;
  font-size: 1rem;
  background-color: #c8e6c9;
  cursor: pointer;
  transition-property: background-color;
  transition-duration: 150ms;
  position: relative;
}

.tab:hover {
  background-color: #a5d6a7;
}

.tab--active {
  background-color: #4caf50;
  color: #ffffff;
}

.tab--active:hover {
  background-color: #4caf50;
}

.tab__indicator {
  background-color: #2e7d32;
  height: 100%;
  position: absolute;
  right: 0;
  width: 0.25rem;
}

.tabs-display__content {
  flex-grow: 1;
  background-color: #f5f5f5;
  padding: 1.5rem;
  overflow-y: auto;
}

.tabs-display__content-title {
  color: #2e7d32;
  font-size: 2rem;
  line-height: 100%;
  margin-bottom: 1.5rem;
}

.tabs-display__content-html {
  font-size: 1.1875rem;
  font-weight: 300;
  line-height: 200%;
}
@media screen and (max-width: 900px) {
  .tabs-display__content-html {
    font-size: 1rem;
  }
}

.tabs-display__content-html >>> p {
  margin-bottom: 0.75rem;
}
</style>
