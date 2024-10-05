<template>
  <div class="discount-day">
  <h1>Скидки дня</h1>
    <p class="p1">23 предложения</p>
    <div class="cards">
      <div v-for="card in cards">
        <discount-card
            :title="card.title"
            :description="card.description"
            :discount-type="card.discountType"
            :discount="card.discount"
            :img="card.img"/>
      </div>
    </div>
    <div class="btn-pos">
      <button class="btn">Показать все</button>
    </div>

  </div>
</template>

<script>
import DiscountCard from "../components-components/discountCard.vue";

export default {
  components: {DiscountCard},
  data(){
  return{
  cards: [
    {img: '/Korzinka.png', title: 'Korzinka.uz', discount: 'В четверг скидки на рыбу', discountType: 'Скидки', description: 'Супермаркеты'},
    {img: '/Mango.png', title: 'MANGO', discount: 'Акция 1+1', discountType: 'Акции', description: 'Магазины брендовой одежды'},
    {img: '/Texnomart.png', title: 'TEXNOMART', discount: 'До — 60% на бытовую технику в ТЦ «Samarkand Darvoza»', discountType: 'Скидки', description: 'Магазины электроники и бытовой техники'},
    {img: '/Makro.png', title: 'Makro', discount: 'При покупке CIF пачка губок Salixan БЕСПЛАТНО', discountType: 'Акции', description: 'Супермаркеты'},
  ]
  }
  }
}
</script>

<style lang="scss" scoped>
.cards{
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  row-gap: 20px;
}
h1{
  font-size: 44px;
  font-weight: 700;
  color: #023131;
  margin-bottom: 5px;
}
.p1{
  font-size: 16px;
  font-weight: 700;
  color: #607282;
  margin-bottom: 20px;
}
.btn{
  color: #3c5858;
  background: #ffff;
  font-weight: 700;
  border-radius: 15px;
  border: none;
  padding: 16px 24px;
  cursor: pointer;
  position: relative;
  margin-left: 10px;
  margin-top: 20px;
}

.btn::after{
  content: '';
  position: absolute;
  right: -10px;
  width: 8px;
  height: 8px;
  background: #607282;
  border-radius: 50%;
  border: 8px solid #f0f6f6;
}
.btn:hover::after{
  content: url("/public/arrow-right.svg");
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 2px;
  position: absolute;
  top: 7px;
  right: -20px;
  padding: 15px;
  padding-bottom: 13.5px;
  border: 1px solid #607282;
}
.discount-day{
  background: #f0f6f6;
  width: 250px;
  padding: 20px;
  margin-bottom: 0;
}
@media (max-width: 500px) {
  h1{
    font-size: 40px;
  }
  .cards{
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    column-gap: 0;
  }
  .discount-day{
    width: 94%;
    padding: 10px 10px 50px 10px;
  }
  .btn-pos{
    text-align: center;
  }
  .btn:hover::after{
    padding: 8px;
    top: 8px;
    right: -10px;
  }
  .btn::after{
    top: 12px;
  }
}
</style>