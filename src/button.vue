<template>
  <button class="g-button" :class="{[`icon-${iconPosition}`]:true}">
    <svg class="icon" v-if="icon">
      <use :xlink:href="`#i-${icon}`"></use>
    </svg>
    <span class="content">
      <slot></slot>
    </span>
  </button>
</template>

<script>
export default {
  props: ['icon', 'iconPosition']
}
</script>

<style lang="scss">
.g-button {
  font-size: var(--font-size);
  height: var(--button-height);
  line-height: var(--button-height);
  background: var(--button-bg);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  align-items: center;
  display: inline-flex;
  justify-content: center;
  vertical-align: top;

  > .icon {
    order: 1;
    margin-right: .3em;
  }

  > .content {
    order: 2;
  }

  &.icon-right {
    > .icon {
      order: 2;
      margin-right: 0;
      margin-left: .3em;
    }

    > .content {
      order: 1;
    }
  }

  &:hover {
    border-color: var(--border-color-hover);
  }

  &:active {
    background-color: var(--button-active-bg);
  }

  &:focus {
    outline: none;
  }
}
</style>