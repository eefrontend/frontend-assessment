<template>
  <div class="accordion-display">
    <div v-for="(item, index) in data" :key="index">
      <button
        :class="[
          'accordion-display__panel',
          { 'accordion-display__panel--active': activeKey === index },
        ]"
        @click="onChangeActiveKey(index)"
        :id="`accordion-header-${index}`"
        :aria-expanded="activeKey === index ? 'true' : 'false'"
        :aria-controls="`accordion-panel-${index}`"
      >
        {{ item.title }}

        <div
          class="accordion-display__panel-indicator"
          v-show="activeKey === index"
        />
      </button>

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
          :id="`accordion-panel-${index}`"
          :aria-labelledby="`accordion-header-${index}`"
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

<style lang="scss" scoped>
.accordion-display {
  &__panel {
    @include button-focus;

    width: 100%;
    height: 4rem;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 1.5rem;
    font-size: $font-size-regular;
    background-color: $color-green-1;
    cursor: pointer;
    position: relative;
    transition-property: background-color;
    transition-duration: 150ms;
    position: relative;
  }

  &__panel:hover {
    background-color: $color-green-2;
  }

  &__panel--active {
    background-color: $color-green-3;
    color: $color-white;
  }

  &__panel--active:hover {
    background-color: $color-green-3;
  }

  &__panel-indicator {
    background-color: $color-green-4;
    height: 0.25rem;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }

  &__content {
    background-color: $color-grey-1;
    padding: 1.5rem;
    line-height: 200%;
  }
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
