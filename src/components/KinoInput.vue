<template>
    <div class="option" >
        <input type="text" class="main-input" placeholder="Введите название фильма" v-on:keyup.enter="sendQuery">
        <span class="search-icon" @click="sendQuery"></span>
        <span class="delete-input-button" @click="deleteInput"></span>
        <span class="filter-icon" @click="filterRating"></span>
        <div></div>
    </div>
</template>


<script>
export default {
    name:"KinoInput",
    methods:{
        sendQuery() {
            let InputFilm = document.querySelector('.main-input')
            let query=InputFilm.value

            if(InputFilm.value==''){
                InputFilm.classList.add('red')

            }
            else{
            this.$emit('send-query', query)
            InputFilm.value=''
            InputFilm.classList.remove('red')
            }
        },
        filterRating(){
            this.$emit('filter-rating')
        },
        deleteInput(){
            let InputFilm = document.querySelector('.main-input')
            InputFilm.value=''
        }
    }
}
</script>


<style>
.option{
     position: relative;
     width: 100%;
     display: flex;
    align-items: center;
    justify-content: center;
    margin: 15px 0;
     
}
.main-input.red{
    border: 2px solid red;
}
.main-input.red::placeholder{
    color: red;
}
.main-input{
    background: #FFFFFF;
    border: 2px solid #FF5C00;
    box-sizing: border-box;
    border-radius: 50px;
    height: 6vh;
    width: 40%;
     outline: none;
    -webkit-appearance: none;
    width: 60%;
    vertical-align: middle;
    padding-left: 20px;

}
.main-input::placeholder{
    font-family: 'Montserrat';
    font-weight: 400;
    font-size: 15px;
    color: #818181;
}
.search-icon {
    position: absolute;
    background-size: cover;
    background-image: url("@/assets/img/search.svg");
    content: "";
    width: 1.5vw;
    height: 1.5vw;
    top: 0.6vw;
    right: 23vw;
}
.delete-input-button{
    position: absolute;
    background-size: cover;
    background-image: url("@/assets/img/cross.svg");
    content: "";
    width: 2vw;
    height: 2vw;
    top: 0.5vw;
    right: 26vw;
}
.filter-icon{
    background-image: url("@/assets/img/filter.svg");
    background-size: cover;
    width: 2vw;
    height: 2vw;
    margin-left: 2vw;

}
@media (max-width:1070px){
  .search-icon{
      top: 0.8vw
  }
}
</style>