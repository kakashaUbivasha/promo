<template>
  <div class="main-wrapper">
  <a-header/>
    <div class="main-content">
      <discounts-day/>
      <discount-top/>
    </div>
  </div>
</template>

<script>
import AHeader from "../components/page-component/aHeader.vue";
import DiscountsDay from "../components/page-component/discountsDay.vue";
import DiscountTop from "../components/page-component/discountTop.vue";
export default {
  components: {DiscountsDay, AHeader, DiscountTop}

}
</script>

<style lang="scss" scoped>
.main-wrapper{
  max-width: 1300px;
  margin: 0 auto;
}
.main-content{
  display: flex;
  gap: 30px;
}
@media (max-width: 500px) {
  .main-content{
    flex-direction: column;
  }
}
</style>