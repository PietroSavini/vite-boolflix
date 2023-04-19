<script>
import { store } from '../store';
    export default{
        data(){
            return{
                store

            }
        },
        props:{
            tv: Object,
        }
        
    }
</script>

<template>
    <div class="ms_card">
        <img :src="`${store.imgUrl}${tv.poster_path}`" alt="">
    </div>
</template>

<style scoped lang="scss">
    
</style>