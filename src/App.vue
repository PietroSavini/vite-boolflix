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
      if(this.store.searchInput === ""){
          this.apiRequest();
      }else{
          this.newRequest();
        }
      },  
    

    newRequest(){
      const params = {
        api_key : this.store.key,
        query : this.store.searchInput,
      }
      
      axios.get(store.moviesUrl,{params}).then((resp)=>{
      this.store.movies = resp.data.results
      })

      axios.get(store.seriesUrl,{params}).then((resp)=>{
      this.store.series = resp.data.results
      })
    },

    apiRequest(){
      const params= {
      api_key : this.store.key,
      query: "a"
      }
      axios.get(store.moviesUrl,{params}).then((resp)=>{
        this.store.movies = resp.data.results
      })
      axios.get(store.seriesUrl,{params}).then((resp)=>{
        this.store.series = resp.data.results
      })

    },
  },

  mounted(){
    this.apiRequest()
  }
}
</script>

<template>
    <AppHeader @search="newSearch"/>
    <main class="d-flex flex-column">
      <AppMain/>
    </main>
    
</template>

<style lang="scss">
@use "./styles/general.scss" as *;

main{
  height: calc(100% - 100px);

}
</style>
