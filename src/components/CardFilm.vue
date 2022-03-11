<template>
    <div class="card-film">
        <div class="card-film-img" :style='{ backgroundImage: `url(${film.posterUrl})` }'></div>
        <p class="card-film-title"> {{ film.nameRu }} </p>
        <div class="card-film-rating__wrapper">
            <img class="card-film-rating-img" src="@/assets/img/rating2.svg" alt="">
            <p class="card-film-rating-title">{{film.rating}}</p>
        </div>
       <div class="card-film-button" @click="show">Подробнее</div>
    </div>
</template>


<script>
export default {
    name:"CardFilm",
    props: {
        film: {type:Object}
    },
    components:{
    },
     methods: {
        show (){
            this.$emit('check-info',this.film)
            this.$modal.show('modal-film');
        },
    },
}
</script>
<style>
.card-film{
    width: 20%;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 10px;
    margin: 10px;
    background-color: #fff;
    justify-content: space-between;
    }
.card-film-img{
    background-size: cover;
    width: 100%;
    height: 56vh;
    border-radius: 10px 10px 0px 0px;

}
.card-film-title{
    font-family: 'Montserrat';
    font-weight: 400;
    font-size: 20px;
    color: #000000;
}
.card-film-rating__wrapper{
    display: flex;
    flex-direction: row;
    align-items:center;
}
.card-film-rating-img{
    width:2vw;
    height: 3vw;
    margin-right: 1vw;
    cursor: default;
}
.card-film-button{
    display: inline-block;
    width: 100%;
    height: 10vh;
    background-color: orange;
    border-radius: 0px 0px 10px 10px;
    font-family: 'Montserrat';
    font-weight: 700;
    font-size: 20px;
    color: #FFFFFF;
    vertical-align: middle;
    text-align: center;
    line-height: 60px;
    cursor: pointer;

}
@media (max-width:900px){
  .card-film{
      width: 28%;
  }
}
</style>