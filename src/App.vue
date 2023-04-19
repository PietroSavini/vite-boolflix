<script >
import axios from "axios";
import {store} from "./store.js";
import AppHeader from "./components/AppHeader.vue";
import AppMain from"./components/AppMain.vue";
export default{

  data(){
    return{
      store,

    }
  },
  components:{
    AppHeader,
    AppMain
  },
  methods:{
    newSearch(){

    },

    apiRequest(){
      const params={
        api_key : this.store.key,
        query: "a"
      }
      axios.get(store.moviesUrl,{params}).then((resp)=>{
        this.store.movies = resp.data.results
        console.log(resp.data.results)
        console.log("films")
        
      })
      axios.get(store.seriesUrl,{params}).then((resp)=>{
        this.store.movies = resp.data.results
        console.log(resp.data.results )
        console.log("serie")
        
      })

    }
  },
  mounted(){
    this.apiRequest()
  }
}
</script>

<template>
    <AppHeader @serach="newSearch"/>
    <main>
      <AppMain/>
    </main>
</template>

<style lang="scss">
@use "./styles/general.scss" as *;

#app{
  height: 100vh;
  width: 100%;
}

main{
  height: calc(100% - 100px);
  position: relative;
}
</style>
