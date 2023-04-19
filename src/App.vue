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
  mounted(){
     
  }
}
</script>

<template>
    <AppHeader/>
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
