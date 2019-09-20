<template>
  <div class="modal">
    <div class="modal__feature">
      <slot name="feature">Detail Feature</slot>
    </div>
    <div class="modal__content">
      <slot name="content">Default Content</slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  methods: {
    close () {
      this.$emit('closeModal');
    },
  },
};
</script>

<style lang="scss" scoped>
  .modal {
    position: fixed;
    width: 100%;
    min-height: 100vh;
    left: 0;
    top: 0;
    background: $white;
    padding: calculateRem(66px) calculateRem(24px);

    @include lg {
      display: flex;
      padding: 0;
      height: 100vh;
    }

    &__feature {

      @include lg {
        max-width: 514px;
      }
    }

    &__content {
      flex-grow: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top:calculateRem(24px);

      @include lg {
        padding: calculateRem(66px) 0;
        align-items: initial;
        min-height: 100vh;
        overflow-y: scroll;
      }
    }
  }
</style>
