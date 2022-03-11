<template>
     <header>
      <div class="header__title__wraper">
        <p class="header-title">Кинопоиск API</p>
        <img class="header-img" src="@/assets/img/popcorn.svg" alt="">
      </div>
      <button @click="movieTop"  class="top-rate-button">Топ фильмов</button>
    </header>
</template>
<script>
export default {
    name:'HeaderFilm',
    methods:{
        movieTop(){
            this.$emit('movie-top')
        }
    }
}
</script>
<style>
header{
  background-color: #fff;
  max-height: 80px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-evenly;
}
.header-title{
  font-family: 'Montserrat';
  font-weight: 400;
  font-size: 40px;
  line-height: 73px;
  color: #000000;
  text-decoration: underline #EB731C;
}
.header__title__wraper{
  display: flex;
}
.header-img{
  width: 50px;
  margin-left: 5vw;
}
</style>