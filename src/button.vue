<template>
  <button @click="$emit('click')" class="g-button" :class="{[`icon-${iconPosition}`]:true}">
    <g-icon class="icon" v-if="icon && !loading" :name="icon"></g-icon>
    <g-icon name="loading" class="loading icon" v-if="loading"></g-icon>
    <span class="content">
      <slot></slot>
    </span>
  </button>
</template>

<script>
import gIcon from './icon.vue'

export default {
  components: {
    'g-icon': gIcon
  },
  props: {
    icon: {},
    loading: {
      type: Boolean,
      default: false
    },
    iconPosition: {
      type: String,
      default: 'left',
      //属性的检查器
      validator(value) {
        return value === 'left' || value === 'right';
      }
    }
  }
}
</script>

<style lang="scss">
@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

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

  .loading {
    animation: spin 2s linear infinite;
  }
}
</style>