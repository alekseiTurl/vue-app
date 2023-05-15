<template>
  <!-- eslint-disable max-len -->
  <ul class="catalog__list">

    <ProductItem v-for="(product) in products" :product="product" :key="product.id" />

  </ul>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
  name: 'ProductList',
  props: ['products'],
  components: { ProductItem },
};
</script>
