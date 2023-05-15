<template>
  <div class="cart__block">
    <ul class="cart__orders">
      <li v-for="item in products" :key="item.productId" :item="item" class="cart__order">
        <h3> {{ item.product.title }}</h3>
        <b>{{ (item.quantity * item.product.price) | numberFormat }} ₽</b>
        <span>Артикул: {{ item.product.id }}</span>
      </li>
    </ul>

    <div class="cart__total">
      <p>Доставка: <b>500 ₽</b></p>
      <p>Итого:
        <b>{{ products.length }}</b>
        <span v-if="products.length === 1"> товар на сумму </span>
        <span v-else-if="products.length >= 5"> товаров на сумму </span>
        <span v-else> товара на сумму </span>

        <b>{{ totalprice | numberFormat }} ₽</b>
      </p>
    </div>

    <button class="cart__button button button--primery" type="submit">
      Оформить заказ
    </button>
  </div>
</template>

<script>
import numberFormat from '@/helpers/numberFormat';

export default {
  props: ['products', 'totalprice'],
  filters: { numberFormat },
};
</script>
