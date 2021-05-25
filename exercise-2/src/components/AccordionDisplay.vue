<template>
  <div class="accordion-display">
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

        <div
          class="accordion-display__panel-indicator"
          v-show="activeKey === index"
        />
      </div>

      <transition
        name="accordion"
        @enter="transitionStart"
        @after-enter="transitionEnd"
        @before-leave="transitionStart"
        @after-leave="transitionEnd"
      >
        <div
          class="accordion-display__content-wrapper"
          v-show="activeKey !== null && activeKey === index"
        >
          <div class="accordion-display__content" v-html="item.content" />
        </div>
      </transition>
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
  methods: {
    transitionStart(el) {
      el.style.height = el.scrollHeight + "px";
    },
    transitionEnd(el) {
      el.style.height = "";
    },
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
  position: relative;
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

.accordion-display__panel-indicator {
  background-color: #2e7d32;
  height: 0.25rem;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
}

.accordion-display__content {
  background-color: #f5f5f5;
  padding: 1.5rem;
  line-height: 200%;
}

.accordion-enter-active,
.accordion-leave-active {
  will-change: height, opacity;
  transition: height 0.3s ease, opacity 0.3s ease;
  overflow: hidden;
}

.accordion-enter,
.accordion-leave-to {
  height: 0 !important;
  opacity: 0;
}
</style>
