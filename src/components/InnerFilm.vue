<template>
    <div>
        <div class="film__inner">
            <CardFilm 
            @check-info="CheckInfo"
            v-for="(film,index) in films" :key="index" :film="film"/>
        </div>
    </div>
</template>


<script>
import CardFilm from './CardFilm.vue'
export default {
    name:"InnerFilm",
    components:{
        CardFilm,
    },
    props: {
        films:{type:Array},
    },
    methods:{
        CheckInfo(film){
            this.$emit('check-rate',film)
        }
    }
}
</script>
<style>
.film__inner{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
</style>