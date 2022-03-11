<template>
    <modal name="modal-film">
            <div class="modal-poster" :style='{ backgroundImage: `url(${film.posterUrl})` }'></div>
            <div class="modal__wrapper">
                <p class="modal-text"> Название фильма: {{film.nameRu}} </p>
                <p class="modal-text"> Описание: {{film.description}} </p>
                <p class="modal-text"> Год создания: {{film.year}} </p>
                <p class="modal-text"> Жанр: {{film.genres[0].genre}} </p>
                <p class="modal-text"> Страна: {{film.countries[0].country}} </p>
            </div>
    </modal>
</template>


<script>
export default {
    props: {
        film: {type: Object}
    },
    methods:{
        hide () {
            this.$modal.hide('modal-film');
        },
    }
}
</script>


<style>
.modal-poster{
    width: 50%;
    background-size: cover;
}
.modal-film{
    display: flex;
    width: 100%;
}
.modal__wrapper{
    display:flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    width: 80%;
    padding: 0 2vw;

}
.vm--modal{
    display: flex;
    top: 90px !important;
    left: 206px !important;
    width: 900px !important;
    height: 467px !important;
    border-radius: 20px !important;
}
.modal-text{
    font-family: 'Montserrat';
    font-size: 18px;
    margin: 6px 0;
    text-align: left;
    font-weight: bold;
}
@media (max-width:1100px){
  .vm--modal{
    top: 6vw!important;
    left: 8vw !important;
    width: 85vw !important;
    height: 50vw !important;
  }
  .modal-text{
    font-size: 2vw;
}
}
</style>