<template>
<fieldset class="field">
  <label class="field__label" :for="input_name" v-html="label">
  </label>
  <input class="field__input" :type="type" :value="value" :id="input_name" :placeholder="placeholder" :required="required" :aria-required="required" :name="input_name" @input="$emit('input', $event.target.value)">
</fieldset>
</template>

<script>
export default {
  name: 'InputField',
  props: {
    value: {
      required: true,
      type: String,
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
    required: {
      type: Boolean,
      default: false,
    },
    type: {
      type: String,
      default: 'text',
    },
    placeholder: String,
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
  margin: 0;
  margin-bottom: calculateRem(15px);
  border: none;
  padding: 0;
  width: 100%;

  & + .field {
    margin-left: calculateRem(16px);
  }

  &__label {
    @include font-size(15px);
    display: block;
    font-weight: 700;
    color: $black;
    margin-bottom: calculateRem(13px);
  }

  &__input {
    @include font-size(14px);
    width: 100%;
    outline: none;
    appearance: none;
    background-color: $gray3;
    border-radius: 8px;
    box-shadow: inset 0px 2px 3px rgba(0, 0, 0, 0.03);
    border: none;
    padding: 10px 15px;
    color: #444;
  }
}

</style>
