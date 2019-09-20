<template>
  <div class="field">
    <input type="checkbox" class="field__input" :checked="value" :name="input_name" :id="input_name" @change="$emit('input', $event.target.checked)">
    <label class="field__label" :for="input_name" v-html="label"></label>
  </div>
</template>

<script>
export default {
  name: 'InputCheckbox',
  props: {
    value: {
      type: Boolean,
      default: false,
    },
    label: {
      type: String,
      default: 'Input Label',
      required: true,
    },
    name: {
      type: String,
      default: '',
      required: true,
    },
  },
  computed: {
    input_name: {
      get () {
        return this.name.replace(/\s/g, '-').toLowerCase();
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.field {
  display: flex;
  position: relative;

  &__label {
    color: $gray5;
    position: relative;
    left: 24px;
    width: calc(100% - 24px);
    font-size: calculateRem(14px);
    font-weight: 400;

  &::before {
      content: '';
      left: -24px;
      top: 2px;
      display: block;
      position: absolute;
      width: 16px;
      height: 16px;
      border: 1px solid #D0D0D0;
      border-radius: 2px;
    }
  }

  &__input {
    position: absolute;
    opacity: 0;

    &:checked + .field__label::before {
      background-image: url('../assets/check.svg');
      background-size: 75%;
      background-repeat: no-repeat;
      background-position: center;
    }
  }
}
</style>
