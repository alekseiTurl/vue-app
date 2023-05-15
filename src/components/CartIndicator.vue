<template>
  <router-link class="header__cart" aria-label="Корзина с товарами" :to="{ name: 'cart' }">
    <svg width="30" height="21" fill="currentColor">
      <use xlink:href="#icon-cart"></use>
    </svg>
    <span class="header__count preloader-cart"
      v-if="$store.state.productAddSending">{{ $store.state.cartProducts.length }}</span>
    <span class="header__count" aria-label="Количество товаров" v-else>{{ $store.state.cartProducts.length }}</span>
  </router-link>
</template>

<script>
export default {

};
</script>
