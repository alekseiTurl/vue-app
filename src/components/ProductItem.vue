<template>
  <!-- eslint-disable max-len -->
  <!-- eslint-disable vuejs-accessibility/label-has-for -->

  <li class="catalog__item" :product="product">
    <router-link class="catalog__pic" :to="{ name: 'product', params: { id: product.id } }">
      <img class="product__img" :src="product.image" :alt="product.title">
    </router-link>

    <h3 class="catalog__title">
      <a href="#">
        {{ product.title }}
      </a>
    </h3>

    <span class="catalog__price">
      {{ product.price | numberFormat }}
    </span>

    <ul class="colors colors--black">
      <li class="colors__item" v-for="color in product.colors" :key="color.id">
        <label class="colors__label">
          <input class="colors__radio sr-only" type="radio" name="color" :value="color.code">
          <span class="colors__value" :style="{ backgroundColor: color.code }">
          </span>
        </label>
      </li>
    </ul>
  </li>
</template>

<script>
import gotoPage from '@/helpers/gotoPage';
import numberFormat from '@/helpers/numberFormat';

export default {
  data() {
    return {

    };
  },
  filters: { numberFormat },
  methods: {
    gotoPage,
  },
  props: ['product'],
};
</script>
