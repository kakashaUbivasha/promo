<template>
  <div class="discount-top">
  <div class="top-disc">
    <h1 class="title-h1">Топовые скидки</h1>
    <ul>
      <li
          v-for="(item, index) in items"
          :key="index"
          :class="{ selected: selectedIndex === index }"
          @click="selectItem(index)"
      >
        {{ item }}
      </li>
    </ul>
    <div v-if="selectedIndex === 0" class="cards">
      <swiper
          :modules="swiperModules"
          :slides-per-view="slidesPerView"
          :space-between="20"
          :navigation="{
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }"
          :pagination="{ clickable: true, el: '.swiper-pagination' }"
          :breakpoints="swiperBreakpoints"
      >
        <swiper-slide v-for="(card, index) in cards1" :key="index">
          <discount-top-card
              :title="card.title"
              :description="card.description"
              :discount-type="card.discountType"
              :discount="card.discount"
              :img="card.img"
              :date="card.date"
              :is-active-date="card.isActive"
          />
        </swiper-slide>
      </swiper>
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
      <div class="swiper-pagination"></div>
    </div>
    <div v-if="selectedIndex === 2" class="cards">
      <swiper
          :modules="swiperModules"
          :slides-per-view="slidesPerView"
          :space-between="20"
          :navigation="{
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }"
          :pagination="{ clickable: true, el: '.swiper-pagination' }"
          :breakpoints="swiperBreakpoints"
      >
        <swiper-slide v-for="(card, index) in cards" :key="index">
          <discount-top-card
              :title="card.title"
              :description="card.description"
              :discount-type="card.discountType"
              :discount="card.discount"
              :img="card.img"
              :date="card.date"
              :is-active-date="card.isActive"
          />
        </swiper-slide>
      </swiper>
      <div class="swiper-button-prev"></div>
      <div class="swiper-button-next"></div>
      <div class="swiper-pagination"></div>
    </div>
  </div>
    <div class="second-block">
      <h3 class="second-block-title">Добро пожаловать на сайт</h3>
      <p class="second-title-text1">Ваш надёжный помощник в поиске лучших скидок и акций различных компаний!</p>
      <p class="second-title-text2">Мы собрали для вас все самые выгодные предложения, чтобы вы могли сэкономить свои деньги и получить максимум удовольствия от покупок.</p>
      <p v-if="isOpen" class="second-title-text2  ">
        Почему СЛЕПОЙ негр не умеет читать?
        Потому что он НЕГР
      </p>
      <span class="second-block-span" @click="toggleText">
      {{ isOpen ? "Свернуть текст" : "Развернуть текст" }}
    </span>
    </div>
    <div class="third-block">
      <h3 class="third-block-title">FAQ</h3>
      <div class="faqs">

        <discount-faq-item :title="'Какие компании представлены на сайте?'">
          <div class="text">
            <p>Чтобы быть в курсе новых скидок и акций на сайте, вы можете подписаться на наш <span style="color: #FF2E4c">телеграм-канал</span> или следить за новостями.</p>

            <p>Мы регулярно отправляем информацию о новых предложениях и акциях нашим подписчикам, чтобы они всегда могли быть в курсе последних скидок и эксклюзивных предложений.</p>

            <p>Также можно регулярно посещать сайт и проверять разделы с акциями и скидками</p>
          </div>

        </discount-faq-item>
        <discount-faq-item :title="'Как я могу быть в курсе новых скидок и акций на сайте?'">
          <div class="text">
            <p>Чтобы быть в курсе новых скидок и акций на сайте, вы можете подписаться на наш <span style="color: #FF2E4c">телеграм-канал</span> или следить за новостями.</p>

            <p>Мы регулярно отправляем информацию о новых предложениях и акциях нашим подписчикам, чтобы они всегда могли быть в курсе последних скидок и эксклюзивных предложений.</p>

            <p>Также можно регулярно посещать сайт и проверять разделы с акциями и скидками</p>
          </div>
        </discount-faq-item>
        <discount-faq-item :title="'Могу ли я поделиться найденными скидками и акциями с друзьями?'">
          <div class="text">
            <p>Чтобы быть в курсе новых скидок и акций на сайте, вы можете подписаться на наш <span style="color: #FF2E4c">телеграм-канал</span> или следить за новостями.</p>

            <p>Мы регулярно отправляем информацию о новых предложениях и акциях нашим подписчикам, чтобы они всегда могли быть в курсе последних скидок и эксклюзивных предложений.</p>

            <p>Также можно регулярно посещать сайт и проверять разделы с акциями и скидками</p>
          </div>
        </discount-faq-item>
      </div>
    </div>
  </div>
</template>

<script>
import DiscountCard from "../components-components/discountCard.vue";
import DiscountTopCard from "../components-components/discountTopCard.vue";
import DiscountFaqItem from "../components-components/discountFaqItem.vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

export default {
  components: {DiscountFaqItem, DiscountTopCard, DiscountCard, Swiper, SwiperSlide},
  data() {
    return {
      items: ["Питание", "Связь", "Магазины"],
      swiperModules: [Navigation, Pagination],
      selectedIndex: 0,
      isOpen: false,
      slidesPerView: 3,
      swiperBreakpoints: {
        360: {
          slidesPerView: 1,
          spaceBetween: 10
        },
        768: {
          slidesPerView: 2,
          spaceBetween: 15
        },
        1024: {
          slidesPerView: 3,
          spaceBetween: 20
        }
      },
      cards1: [
        {img: './public/gosty.png', title: 'Gosty', discount: 'Каждый вторник — 20% на все меню', discountType: 'Скидки', description: 'Рестораны', date: 'До 29 февраля', isActive: false},
        {img: './public/shosh.png', title: 'Shosh', discount: 'Скидки на еду и напитки', discountType: 'Скидки', description: 'Кафе', date: '71:59:59', isActive: true},
        {img: './public/petrovich.png', title: 'Petrovich', discount: 'Ланч по выгодной цене и 2% кешбэк по промокоду', discountType: 'Скидки', description: 'Рестораны', date: 'До 29 февраля', isActive: false},
        {img: './public/shosh.png', title: 'Shosh', discount: 'Скидки на еду и напитки', discountType: 'Скидки', description: 'Кафе', date: '71:59:59', isActive: true},
        {img: './public/petrovich.png', title: 'Petrovich', discount: 'Ланч по выгодной цене и 2% кешбэк по промокоду', discountType: 'Скидки', description: 'Рестораны', date: 'До 29 февраля', isActive: false},
      ],
      cards: [
        {img: './public/Korzinka.png', title: 'Korzinka.uz', discount: 'В четверг скидки на рыбу', discountType: 'Скидки', description: 'Супермаркеты', date: 'До 29 февраля', isActive: false},
        {img: './public/Mango.png', title: 'MANGO', discount: 'Акция 1+1', discountType: 'Акции', description: 'Магазины брендовой одежды', date: '71:59:59', isActive: true},
        {img: './public/Texnomart.png', title: 'TEXNOMART', discount: 'До — 60% на бытовую технику в ТЦ «Samarkand Darvoza»', discountType: 'Скидки', description: 'Магазины электроники и бытовой техники', date: 'До 29 февраля', isActive: false},
        {img: './public/Makro.png', title: 'Makro', discount: 'При покупке CIF пачка губок Salixan БЕСПЛАТНО', discountType: 'Акции', description: 'Супермаркеты', date: 'До 29 февраля', isActive: false},
      ],
      faqs: [
        {title: 'Какие компании представлены на сайте?', content: 'The US labor market added far more jobs than projected in September while the unemployment rate unexpectedly ticked lower, reflecting a stronger picture of the jobs market than Wall Street had expected.\n' +
              '\n' +
              'Data from the Bureau of Labor Statistics released Friday showed the labor market added 254,000 payrolls in September, more additions than the 150,000 expected by economists.'},
        {title: 'Как я могу быть в курсе новых скидок и акций на сайте?', content: 'Чтобы быть в курсе новых скидок и акций на сайте, вы можете подписаться на наш телеграм-канал или следить за новостями.\n' +
              'Мы регулярно отправляем информацию о новых предложениях и акциях нашим подписчикам, чтобы они всегда могли быть в курсе последних скидок и эксклюзивных предложений.\n' +
              'Также можно регулярно посещать сайт и проверять разделы с акциями и скидками'},
        {title: 'Могу ли я поделиться найденными скидками и акциями с друзьями?', content: 'Чтобы быть в курсе новых скидок и акций на сайте, вы можете подписаться на наш телеграм-канал или следить за новостями.\n' +
              'Мы регулярно отправляем информацию о новых предложениях и акциях нашим подписчикам, чтобы они всегда могли быть в курсе последних скидок и эксклюзивных предложений.\n' +
              'Также можно регулярно посещать сайт и проверять разделы с акциями и скидками'},
      ]
    };
  },
  methods: {
    selectItem(index) {
      this.selectedIndex = index;
    },
    toggleText(){
    this.isOpen = !this.isOpen
    }
  },
}
</script>

<style lang="scss" scoped>

.cards{
  display: flex;
  gap: 20px;
}
.title-h1{
  font-size: 44px;
  font-weight: 700;
  color: #248888;
  border-bottom: 1px solid #bedada;
  padding-bottom: 20px;
}
ul {
  list-style: none;
  padding: 0;
  display: flex;
  padding-bottom: 30px;
}

li {
  padding: 10px;
  position: relative;
  cursor: pointer;
  transition: color 0.3s ease;
  text-transform: uppercase;
  color: #001c1c;
  font-size: 20px;
}
.selected {
  color: #3c5858;
}
.selected::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 8px;
  height: 8px;
  background-color: #FF2E4c;
  border-radius: 50%;
}
.discount-top{
  width: 75%;
  margin-top: 40px;
  padding-bottom: 50px;
}
.top-disc{
  padding: 30px;
  background: #f0f6f6;
  border-radius: 10px;
  position: relative;
}
.second-block{
  margin-top: 70px;
  display: flex;
  flex-direction: column;
  gap: 13px;
}
.second-block-title{
  font-size: 28px;
  font-weight: 700;
  color: #023131;
}
.second-title-text1{
  font-size: 18px;
  font-weight: 700;
  color: #001c1c;
}
.second-title-text2{
  font-size: 17px;
  color: #3c5858;
}
.second-block-span{
  font-size: 17px;
  color: #607282;
  cursor: pointer;
}
.faqs{
  display: flex;
  flex-direction: column;
  gap: 30px;
}
.third-block-title{
  font-size: 44px;
  font-weight: 700;
  color: #023131;
}
.third-block{
  margin-top: 60px;
}
.text{
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 750px;
}

@media (max-width: 500px){
  .discount-top{
    width: 329px;
    margin: 0 auto;
  }
  .title-h1{
    font-size: 40px;
  }
  ul{
    overflow-x: auto;
  }
}

</style>