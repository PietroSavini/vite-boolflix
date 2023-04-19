<script>
import { store } from '../store';
    export default {
        data(){
            return{
                store
            }
        }
    }
</script>

<template>
    <header>
        <div class="container d-flex justify-content-between align-items-center">
            <div class="logo">
                <h1>Bool<span>Flix</span></h1>
            </div>
            <div class="search-bar">
                <input type="text" name="" id="" v-model.trim="store.serachInput" placeholder=" cerca un film o una serie tv" >
            </div>
        </div>
    </header>
</template>

<style scoped lang="scss">
    header{
       height: 100px; 
       background-color: black;
       box-shadow: 0px 0px 10px black;
       .container{
        height: 100%;
        .logo {
            h1{
                color: #fff;
            }
            span{
            color:red;
            }
        }
        .search-bar{
            width: 30%;
            input[type="text"]{
                background: rgb(85, 83, 83);
                border: 1px solid #fff;
                border-radius:5px;
                width: 100%;
                color:#fff;
            }
        }

       }
    }
    
</style>