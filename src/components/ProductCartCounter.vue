<template>
  <!-- eslint-disable max-len -->
  <!-- eslint-disable vuejs-accessibility/label-has-for -->
  <!-- eslint-disable vuejs-accessibility/form-control-has-label -->
  <div class="form__counter">
    <button :style="styleObject" type="button" aria-label="Убрать один товар" @click="updateDecrement">
      <svg width="12" height="12" fill="currentColor">
        <use xlink:href="#icon-minus"></use>
      </svg>
    </button>

    <input :value="productAmount" @input="$emit('update:productAmount', event.target.value)" />

    <button :style="styleObject" type="button" aria-label="Добавить один товар" @click="updateIncrement">
      <svg width="12" height="12" fill="currentColor">
        <use xlink:href="#icon-plus"></use>
      </svg>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      styleObject: {
        cursor: 'pointer',
      },
    };
  },

  props: {
    productAmount: {
      type: Number,
      required: true,
    },
  },
  methods: {
    updateIncrement() {
      this.$emit('update:productAmount', this.productAmount + 1);
    },
    updateDecrement() {
      if (this.productAmount > 1) {
        this.$emit('update:productAmount', this.productAmount - 1);
      }
    },
  },
};
</script>
