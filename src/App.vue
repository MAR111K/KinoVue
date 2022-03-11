<template>
  <div id="app">
    <HeaderFilm
    @movie-top="MovieTop"
    >
    </HeaderFilm>


    <ModalFilm :film="this.film">
    </ModalFilm>


    <KinoInput
    @filter-rating="FilterCheck"
    @send-query="getQuery"
    />

    <InnerFilm 
    @check-rate="CheckRate"
    :query="query" 
    :films="films"
    />
  </div>
</template>

<script>
import KinoInput from './components/KinoInput'
import InnerFilm from './components/InnerFilm'
import ModalFilm from './components/ModalFilm.vue'
import HeaderFilm from './components/HeaderFilm.vue'

export default {
  name: 'App',
  components: {
    KinoInput,
    InnerFilm,
    ModalFilm,
    HeaderFilm,
  },
  data(){
    return{
      query: "",
      films:[],
      film: {},
    }
  },
  
  methods: {
    MovieTop(){
      fetch('https://kinopoiskapiunofficial.tech/api/v2.2/films/top?type=TOP_AWAIT_FILMS&page=1', {
        method: 'GET',
        headers: {  
          'X-API-KEY': '',//ввести токен
          'Content-Type': 'application/json',
          },
        })
        .then(res => res.json())
        .then(data => this.films = data.films)
        console.log(this.films)
      
    },
    getQuery(query) {
      fetch(`https://kinopoiskapiunofficial.tech/api/v2.1/films/search-by-keyword?keyword=${query}`, {
                method: 'GET',
                headers: {  
                    'X-API-KEY': '',//ввести токен
                    'Content-Type': 'application/json',
                },
            })
            .then(res => res.json())
            .then(data => this.films = data.films)
      
    },
    CheckRate(film){
      this.film = film
    },
    FilterCheck(){
      this.films.sort((a,b)=>a.rating>b.rating ? -1:1)
    }
    
 
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
body{
  background-color: #212121;
}
.card-film__wrapper{
  width: 90%;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
}
.top-rate-button{
    margin-left: 3%;
    font-size: 1.4vw;
    color: white;
    background-color: orange;
    display: flex;
    font-family: 'Montserrat', sans-serif;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: center;
    width: 15vw;
    height: 2.8vw;
    border: 0;
    border-radius: 100px;
}
</style>
