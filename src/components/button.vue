<template>
  <button
    :type="type"
    :aria-label="content"
    @click="$emit('click')"
    class="button"
    :class="[`button--${variant}`, fullWidth && 'button--full', icon && !iconOnly ? 'button--hasicon' : null]"
  >
    <i v-if="icon" :class="['button__icon', 'fab', `fa-${icon}`]"></i>
    <span v-if="!iconOnly">{{ content }}</span>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    fullWidth: {
      type: Boolean,
      default: false,
    },
    variant: {
      type: String,
      default: 'default',
    },
    type: {
      type: String,
      default: 'button',
    },
    content: {
      type: String,
      default: '',
    },
    icon: {
      type: String,
      default: '',
    },
    iconOnly: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  appearance: none;
}

.button {
  @include font-size($baseFontSize);
  font-weight: 700;
  border-radius: $borderRadius;
  border: none;
  padding: calculateRem(16px);
  text-align: center;
  display: inline-flex;
  justify-content: center;
  position: relative;

  & + .button {
    margin-left: calculateRem(16px);
  }

  &--default {
    background-color: $pink;
    color: $white;
  }

  &--secondary {
    background-color: $blue;
    color: $white;
  }

  &--common {
    background-color: $gray2;
    color: $gray4;
  }

  &--full {
    width: 100%;
  }

  &--hasicon {
    padding-left: calculateRem(32px);

    .button__icon {
      position: absolute;
      left: calculateRem(15px);
      top: calculateRem(18px);
    }
  }
}
</style>
