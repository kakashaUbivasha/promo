<template>
  <div class="collapsible-block">
    <div class="header" @click="toggleBlock">
      <h3 class="header-title">{{ title }}</h3>
      <div class="icon" :class="{ open: isOpen }"></div>
    </div>
    <div v-if="isOpen" class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    }
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    toggleBlock() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.collapsible-block {
  border-bottom: 2px solid #ccc; /* Нижний бордер */
  padding: 10px 0;
}

.header {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
}

.header-title {
  padding-bottom: 25px;
}

.icon {
  width: 32px;
  height: 32px;
  position: relative;
}

.icon::before,
.icon::after {
  content: '';
  position: absolute;
  background-color: #bedada;
  transition: all 0.3s ease;
}
.icon::before {
  width: 100%;
  height: 2px;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
}
.header:hover .icon::before,
.header:hover .icon::after{
  background-color: #FF2E4c;
}
.icon::after {
  height: 100%;
  width: 2px;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
}

.icon.open::before {
  transform: translateY(-50%) rotate(45deg); /* Поворот крестика */
}

.icon.open::after {
  transform: translateX(-50%) rotate(45deg); /* Поворот крестика */
}

.content {
  padding: 10px 0;
  font-size: 18px;
  line-height: 27px;
  margin-left: 40px;
}
@media (max-width: 500px) {
  .icon{
    width: 13px;
    height: 22px;
    padding-left: 15px;
  }
  .header-title{
    padding-bottom: 15px;
    font-size: 20px;

  }
  .header{
    gap: 40px;
  }
  .icon.open::before {
    transform: translateY(-50%) rotate(45deg); /* Поворот крестика */
  }

  .icon.open::after {
    transform: translateX(-50%) rotate(45deg); /* Поворот крестика */
  }
}
</style>
