<template>
  <div class="card">
    <div :style="backgroundImageStyle" class="card-img">
      <span :class="{ selected: isActiveDate }" class="date">{{date}}</span>
    </div>
    <div class="card-text">
      <div class="col-1">
        <h2 class="card-text-title">{{title}}</h2>
        <p class="card-text-discount">{{titleCurrentLength(discount)}}</p>
      </div>
      <div class="col-2">
        <p class="col-2-text p2">{{discountType}}</p>
        <div class="cashback">
          <span class="cashback-text">Кешбэк</span>
          <span class="cashback-count">3%</span>
        </div>
        <p class="col-2-text full-width">{{textCurrentLength(description)}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    img:{
      type: String,
      required: true
    },
    date:{
      type: String,
      required: true
    },
    isActiveDate:{
      type: String,
      required: false
    },
    title: {
      type: String,
      required: true
    },
    discount: {
      type: String,
      required: true
    },
    discountType: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    }
  },
  methods:{
    textCurrentLength(props){
      return props.length > 30 ? props.slice(0, 30) + '...' : props;
    },
    titleCurrentLength(props){
      return props.length > 47 ? props.slice(0, 47) + '...' : props;
    }
  },
  computed:{
    backgroundImageStyle(){
      return{
        backgroundImage: `url(${this.img})`,
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.card{
  cursor: pointer;
}

.card-img{
  border: 1px solid #bedada;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  border-bottom: none;
  width: 290px;
  height: 185px;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
}
.date{
  position: absolute;
  top: 10px;
  left: 10px;
  z-index: 2;
  color: #e1102e;
  padding: 4px 12px 6px 12px;
  background: #ffedef;
  border-radius: 5px;
  font-size: 14px;
  font-weight: 700;
}
.selected{
  color: white;
  background: #FF2E4c;
  border: 1px solid white;
  padding: 4px 15px 6px 15px;

}
.card-text{
  width: 266px;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 12px;
  border: 1px dashed #bedada;
  border-top: none;
  background: white;
  position: relative;
  height: 160px;
}
.card:hover .card-img{
  border-color: #248888;
}
.card:hover .card-text{
  border: 1px solid #248888;
  border-top: none;
}
.col-1{
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}
.card-text-title{
  font-size: 14px;
  font-weight: 500;
  color: #607282;
  text-transform: uppercase;
}
.p2:hover{
  color: #FF2E4c;
}
.card-text-title:hover{
  color: #FF2E4C;
}
.card-text-discount{
  font-size: 18px;
  font-weight: 700;
  color: #001c1c;
}
.card-text-discount:hover{
  color: #248888;
}
.col-2{
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  padding-bottom: 12px;
  row-gap: 5px;
  position: absolute;
  bottom: 10px;
  column-gap: 70px;

}
.col-2-text{
  font-size: 14px;
  font-weight: 400;
  color: #607282;
}
.cashback{
  display: flex;
  justify-content: center;
  align-items: center;
}
.cashback-text{
  font-size: 14px;
  font-weight: 400;
  color: #607282;
  padding: 6px;
  border: 1px solid #607282;
  border-radius: 5px;
}
.cashback-count{
  font-size: 14px;
  font-weight: 700;
  color: white;
  background: #607282;
  padding: 6px;
  border: 1px solid #607282;
  border-radius: 5px;
}
.full-width{
  grid-column: 1 / -1;
}
@media (max-width: 500px) {
  .card-img{
    width: 264px;
  }
  .card-text{
    width: 240px;
  }
  .card-text-title{
    font-size: 18px;
  }
  .col-2{
    column-gap: 50px;
    row-gap: 0;
  }
}
</style>