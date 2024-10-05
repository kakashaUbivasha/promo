<template>
  <div class="header">
  <div class="header-logo">
    Logo
  </div>
    <div class="header-list">
      <ul class="ul1">
        <li class="li1">
          <div class="brg-mnu-all">
            <span class="brg-mnu"></span>
            <span class="brg-mnu"></span>
            <span class="brg-mnu"></span>
          </div>
          Все предложения
        </li>
        <li>Скидки</li>
        <li>Акции</li>
        <li>Промокоды</li>
        <li>Кешбэк</li>
      </ul>
    </div>
    <div class="header-icon-list">
    <ul>
      <li><img src="/public/search.svg" alt="search"/></li>
      <li class="li2"><img src="/public/socials.svg" alt="tg"></li>
      <li class="li2"><img src="/public/Cabinet.svg" alt="Cabinet"></li>
      <li>Ру</li>
      <li class="li3">
        <div class="brg-mnu-all" @click="toggleMenu">
        <span class="brg-mnu"></span>
        <span class="brg-mnu"></span>
        <span class="brg-mnu"></span>
       </div>
      </li>
      <li><button class="btn">Добавить скидку</button></li>
    </ul>
    </div>
    <div class="overlay" :class="{ 'active': isOpen }" @click="toggleMenu"></div>
    <nav class="dropdown-menu" :class="{ 'active': isOpen }">
      <div @click="isOpen=false" class="closebtn">&times;</div>
      <ul>
        <li><a href="#">Скидки</a></li>
        <li><a href="#">Акции</a></li>
        <li><a href="#">Промокоды</a></li>
        <li><a href="#">Кешбэк</a></li>
        <li><button class="btn1">Добавить скидку</button></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
data(){
  return{
    isOpen: false
  }
},
  methods:{
    toggleMenu(){
      this.isOpen = !this.isOpen
    }
  }
}
</script>

<style lang="scss" scoped>
*{
  font-size: 18px;
  font-weight: 400;
}
.li3{
  display: none;
}
.header-logo{
  font-weight: 700;
  font-size: 44px;
  line-height: 50px;
  color: #023131;
  display: flex;
  align-items: center;
}
.brg-mnu{
  width: 18px;
  border: 1.5px solid #FF2E4c;
  position: relative;

}
.brg-mnu::before{
  content: '';
  position: absolute;
  top: -2px;
  left: -10px;
  width: 0.01px;
  border: 2px solid #FF2E4c;
  border-radius: 50%;
}
.brg-mnu-all{
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin-top: 2px;
}
ul{
  list-style: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}
.ul1{
  gap: 20px;
}
li{
  cursor: pointer;
}
.btn{
  color: white;
  background: #FF2E4c;
  font-weight: 700;
  border-radius: 15px;
  border: none;
  padding: 16px 24px;
  cursor: pointer;
  position: relative;
  margin-left: 10px;
}

.btn::after{
  content: '';
  position: absolute;
  right: -10px;
  width: 8px;
  height: 8px;
  background: #607282;
  border-radius: 50%;
  border: 8px solid white;
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
.header{
  display: flex;
  justify-content: space-between;
  margin-bottom: 30px;
}
.dropdown-menu{
  display: none;
}
.li1{
  display: flex;
  gap: 10px;
}
.header-list, .header-icon-list{
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 15px;
}
@media (max-width: 500px) {
  .header-logo{
    font-size: 30px;
    margin-top: 10px;
  }
  .header-list{
    display: none;
  }
  .btn{
    display: none;
  }
  .li2{
    display: none;
  }
  .header{
    margin-left: 15px;


  }
  .li3{
    display: block;
  }
  .brg-mnu::before{
    content: none;
  }
  .brg-mnu{
    width: 18px;
    border: 1.5px solid #248888;
  }
  .brg-mnu-all{
    gap: 4px;
  }
  ul{
    gap: 25px;
  }
  .dropdown-menu {
    display: none;
    position: absolute;
    top: 0px;
    right: 0;
    width: 100%;
    background-color: #fff;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    transform: translateY(-100%);
    transition: transform 0.3s ease;
    z-index: 1000;
  }

  .dropdown-menu ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    padding: 0;
    margin: 20px 0;
  }

  .dropdown-menu ul li {
    padding: 15px;
    border-bottom: 1px solid #ddd;
    text-align: center;
  }
  .dropdown-menu ul li:hover{
    border-bottom: 1px solid #FF2E4c;
  }
  .dropdown-menu ul li a {
    text-decoration: none;
    color: #333;
    font-size: 16px;
  }
  .dropdown-menu ul li a:hover{
    color: #FF2E4c;
  }
  .dropdown-menu ul li:last-child {
    border-bottom: none;
  }
  .dropdown-menu.active {
    display: block;
    transform: translateY(0);
  }
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6);
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s ease, visibility 0.3s ease;
    z-index: 999;
  }

  .overlay.active {
    opacity: 1;
    visibility: visible;
  }
  .closebtn {
    color: black;
    font-weight: bold;
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 26px;
    line-height: 20px;
    cursor: pointer;
    transition: 0.3s;
  }

  .closebtn:hover {
    color: black;
  }
  .btn1{
    color: white;
    background: #FF2E4c;
    font-weight: 700;
    border-radius: 15px;
    border: none;
    padding: 16px 24px;
    cursor: pointer;
    position: relative;
    margin-left: 10px;
  }

  .btn1::after{
    content: '';
    position: absolute;
    right: -10px;
    width: 8px;
    height: 8px;
    background: #607282;
    border-radius: 50%;
    border: 8px solid white;
  }
  .btn1:hover::after{
    content: url("/public/arrow-right.svg");
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 2px;
    position: absolute;
    top: 10px;
    right: -12px;
    padding: 10px;
    border: 1px solid #607282;
  }
}
</style>