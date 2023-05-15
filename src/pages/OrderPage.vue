<template>
  <!-- eslint-disable max-len -->
  <!-- eslint-disable vuejs-accessibility/label-has-for -->
  <main class="content container">
    <div class="content__top">
      <ul class="breadcrumbs">
        <li class="breadcrumbs__item">
          <a class="breadcrumbs__link" href="index.html">
            Каталог
          </a>
        </li>
        <li class="breadcrumbs__item">
          <a class="breadcrumbs__link" href="cart.html">
            Корзина
          </a>
        </li>
        <li class="breadcrumbs__item">
          <a class="breadcrumbs__link">
            Оформление заказа
          </a>
        </li>
      </ul>

      <h1 class="content__title">
        Корзина
      </h1>
      <span class="content__info">
        3 товара
      </span>
    </div>
    <section class="cart position-relative" v-if="formSending">
      <div class="preloader">
        <img src="img/preload.gif" alt="preload">
      </div>
    </section>
    <section class="cart" v-else>
      <form class="cart__form form" action="#" method="POST" @submit.prevent="order">
        <div class="cart__field">
          <div class="cart__data">
            <BaseFormText v-model="formData.name" title="ФИО" :error="formError.name"
              placeholder="Введите ваше полное имя">
            </BaseFormText>
            <BaseFormText v-model="formData.address" title="Адрес доставки" :error="formError.address"
              placeholder="Введите ваш адрес">
            </BaseFormText>
            <BaseFormText v-model="formData.phone" type="tel" title="Телефон" :error="formError.phone"
              placeholder="Введите ваш телефон">
            </BaseFormText>
            <BaseFormText v-model="formData.email" type="email" title="Email" :error="formError.email"
              placeholder="Введите ваш Email">
            </BaseFormText>
            <BaseFormTextarea title="Комментарий к заказу" v-model="formData.comment" :error="formError.comment"
              placeholder="Ваши пожелания"></BaseFormTextarea>

          </div>

          <div class="cart__options">
            <h3 class="cart__title">Доставка</h3>
            <ul class="cart__options options">
              <li class="options__item">
                <label class="options__label">
                  <input class="options__radio sr-only" type="radio" name="delivery" value="0" checked="">
                  <span class="options__value">
                    Самовывоз <b>бесплатно</b>
                  </span>
                </label>
              </li>
              <li class="options__item">
                <label class="options__label">
                  <input class="options__radio sr-only" type="radio" name="delivery" value="500">
                  <span class="options__value">
                    Курьером <b>500 ₽</b>
                  </span>
                </label>
              </li>
            </ul>

            <h3 class="cart__title">Оплата</h3>
            <ul class="cart__options options">
              <li class="options__item">
                <label class="options__label">
                  <input class="options__radio sr-only" type="radio" name="pay" value="card">
                  <span class="options__value">
                    Картой при получении
                  </span>
                </label>
              </li>
              <li class="options__item">
                <label class="options__label">
                  <input class="options__radio sr-only" type="radio" name="pay" value="cash">
                  <span class="options__value">
                    Наличными при получении
                  </span>
                </label>
              </li>
            </ul>
          </div>
        </div>
        <OrderCart :products="orderCart" :totalprice="orderCartPrice"></OrderCart>
        <div class="cart__error form__error-block" v-if="formErrorMessage">
          <h4>Заявка не отправлена!</h4>
          <p>
            {{ formErrorMessage }}
          </p>
        </div>
      </form>
    </section>
  </main>
</template>

<script>
import BaseFormText from '@/components/BaseFormText.vue';
import BaseFormTextarea from '@/components/BaseFormTextarea.vue';
import OrderCart from '@/components/OrderCart.vue';
import { API_BASE_URL } from '@/config';
import axios from 'axios';

export default {
  components: { BaseFormText, BaseFormTextarea, OrderCart },
  data() {
    return {
      formData: {},
      formError: {},
      formErrorMessage: '',
      formSending: false,
    };
  },
  methods: {
    order() {
      this.formError = {};
      this.formErrorMessage = '';
      this.formSending = true;
      return (new Promise((res) => setTimeout(res, 300)))
        .then(() => axios
          .post(`${API_BASE_URL}/api/orders`, {
            ...this.formData,
          }, {
            params: {
              userAccessKey: this.$store.state.userAccessKey,
            },
          })
          .then((response) => {
            this.$store.commit('resetCart');
            this.$store.commit('updateOrderInfo', response.data);
            this.$router.push({ name: 'orderInfo', params: { id: response.data.id } });
            this.formSending = false;
          })
          .catch((error) => {
            this.formError = error.response.data.error.request || {};
            this.formErrorMessage = error.response.data.error.message;
            this.formSending = false;
          }));
    },
  },
  computed: {
    orderCart() {
      return this.$store.state.cartProductsData;
    },
    orderCartPrice() {
      return this.$store.getters.cartTotalPrice;
    },
  },
};
</script>
