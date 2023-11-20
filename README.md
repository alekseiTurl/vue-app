# Technozavr -  Интернет магазин

*[Перейти на сайт ](https://alekseiturl.github.io/vue-app/)*

Web-приложение для компании Технозавр. Проект разработан на Vue.JS V2. Используется REST API.<br/>
Многостраничность реализована по средством VueRouter. Так же используется библиотека управления состояние Vuex<br/>
Web-интерфейс имеет следующие функции:<br/>
* Визуализация списка товаров
* Фильтрация товара по параметрам
* Добавление товара(ов) в корзину
* Изменение количества товаров ( как в корзине, так и на странице продукта)
* Оформление покупки товара

<br/>
На главной странице сайта выводится ProductsList и фильтр продутов по параметрам. Страница товара предоставляет возможность добавление товара в корзину с изменением его количества. В корзину можно перейти как по нажатию кнопки
в шапке сайта, так и со страницы товара. В корзину добавляются все товары выбранные пользователем. Здесь же реализована функция подсчёта стоимости заказа с учётом доставки.<br/> <br/>
На странице корзины реализован преход к оформлению заказа. В форме оформления заказа присутствует валидация. После успешного прохождения валидации и отправки формы на сервер, происходит переход на страницу успешного оформления,
которая содержит информацию о заказе и пользователе.<br/>

<br/>

*Директория docs используется только для демонстрации проекта.*


## Для запуска проекта скачайте файлы репозитория, установите зависимости командой -- npm install. После чего запустите одну из служебных команд: <br/>
*Перед запуском убедитесь, что вы установили Node.js версии 12 или выше.*<br/>

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-- npm run serve : для сборки dev версии :hammer:<br/>
-- npm run build : для сборки prod версии :handbag:

<br/>

## Use Plugins :floppy_disk: :

<br/>
    "axios": "^0.19.2",<br/>
    "core-js": "^3.8.3",<br/>
    "vue": "^2.6.14",<br/>
    "vue-router": "^3.6.5",<br/>
    "vuex": "^3.4.0"<br/>
    "@babel/core": "^7.12.16",<br/>
    "@babel/eslint-parser": "^7.12.16",<br/>
    "@vue/cli-plugin-babel": "~5.0.0",<br/>
    "@vue/cli-plugin-eslint": "~5.0.0",<br/>
    "@vue/cli-service": "~5.0.0",<br/>
    "@vue/eslint-config-airbnb": "^6.0.0",<br/>
    "eslint": "^7.32.0",<br/>
    "eslint-plugin-import": "^2.25.3",<br/>
    "eslint-plugin-vue": "^8.0.3",<br/>
    "eslint-plugin-vuejs-accessibility": "^1.1.0",<br/>
    "sass": "^1.32.7",<br/>
    "sass-loader": "^12.0.0",<br/>
    "vue-template-compiler": "^2.6.14"<br/>
