<template>
  <div class="tabs-display">
    <div>
      <div
        v-for="(item, index) in data"
        :class="[
          'tabs-display__tab',
          { 'tabs-display__tab--active': activeKey === index },
        ]"
        :key="index"
        @click="onChangeActiveKey(index)"
      >
        {{ item.title }}

        <div class="tabs-display__tab-indicator" v-show="activeKey === index" />
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

<style lang="scss" scoped>
.tabs-display {
  display: flex;
  height: 32rem;
  background-color: $color-green-1;
  border: 1px solid $color-green-1;

  &__tab {
    min-width: 12rem;
    height: 4rem;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 1.5rem;
    font-size: $font-size-regular;
    background-color: $color-green-1;
    cursor: pointer;
    transition-property: background-color;
    transition-duration: 150ms;
    position: relative;
  }

  &__tab:hover {
    background-color: $color-green-2;
  }

  &__tab--active {
    background-color: $color-green-3;
    color: $color-white;
  }

  &__tab--active:hover {
    background-color: $color-green-3;
  }

  &__tab-indicator {
    background-color: $color-green-4;
    height: 100%;
    position: absolute;
    right: 0;
    width: 0.25rem;
  }

  &__content {
    flex-grow: 1;
    background-color: $color-grey-1;
    padding: 1.5rem;
    overflow-y: auto;
  }

  &__content-title {
    color: $color-green-4;
    font-size: $font-size-large;
    line-height: 100%;
    margin-bottom: 1.5rem;
  }

  &__content-html {
    font-size: $font-size-small;
    font-weight: 300;
    line-height: 200%;

    @media screen and (max-width: $media-tablet-portrait) {
      font-size: $font-size-regular;
    }
  }

  &__content-html >>> p {
    margin-bottom: 0.75rem;
  }
}
</style>
