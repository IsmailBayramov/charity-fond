<script setup>
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth' // Добавляет плавную анимацию прокрутки
  });
  
};
</script>

<template>
    <header>
        <div class="header-top">
            <img @click="scrollToTop" src="../assets/images/logo.png" class="header-logo" alt="">
            <span @click="scrollToTop" class="header-text">Благотворительный фонд</span>
        </div>
    </header>
</template>

<style scoped>

.header-top {
  display: flex;
  justify-content: center;
  text-align: center;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  padding: 15px;
  background: rgb(224, 224, 224);
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.header-text {
  font-size: calc(1em + 1vw);
  font-weight: 500;
  cursor: pointer;
  /* font-weight: bold; */
}

.header-logo {
  max-width: 2.5em; /* Адаптивная ширина */
  object-fit: contain;
  margin-right: 15px;
  height: auto; /* Сохранение пропорций */
  cursor: pointer;
}

@media screen and (max-width: 600px){
  .header-text {
    display: none;
  }
  
  .header-logo {
    margin-right: 0;
  }
}
</style>
