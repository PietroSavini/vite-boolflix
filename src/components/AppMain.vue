<script>
import { store } from '../store';
import AppCardMovie from "./AppCardMovie.vue";
import AppCardTv from "./AppCardTv.vue"
export default {
    data(){
        return{
            store
        }
    },
    components:{
        AppCardMovie,
        AppCardTv,
    }
}
</script>

<template>
    <section class="jumbotron">
        <div class="container jumbo">
            <div class="row">
                <div class="col-4">
                    <h2 class="jumbo-title"></h2>
                    <h3 class="jumbo-original-title"></h3>
                    <p class="jumbo-description"></p>
                    <span class="rating"></span>
                    <span class="lang"></span>
                </div>
                <div class="col-8"></div>
            </div>
        </div>
    </section>
    
    <section class="results">
        
        <div class="container">
            <h2>Movies</h2>
            <div class="row media-scroller mb-3 flex-nowrap align-items-center">
                <!-- cards for movies -->
                <AppCardMovie v-for="movieCard in store.movies" :movie="movieCard"/>
            </div>
            <h2>TV-Series</h2>
            <div class="row media-scroller flex-nowrap align-items-center mb-3">
                <AppCardTv v-for="tvCard in store.series" :tv="tvCard"/>

            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
    section{
        padding: 2rem 2rem;
    }   
    .jumbotron{
        height: 35%;
        background-color: rgb(0, 0, 0) ;
        padding-top:0;
        .jumbo{
            height: 100%;
            .row{
                height: 100%;
            }
            .col-4{
                overflow-y: auto;
                &::-webkit-scrollbar {
                    width: 0px;
                }
            }
        }  
    }
    
    .results{
        height: 65%;
        padding-bottom: 0;
        z-index: 1;
        box-shadow: inset 0px 0px 20px black;
        background: linear-gradient( rgb(0,0,0)10%,rgb(19, 18, 18) ) ;
       
        
        .container{
            height: 100%;
            color: #fff;
            overflow-y: auto;
            &::-webkit-scrollbar {
            width: 0px;    
        }
            .media-scroller{
                position: relative;
                height: 200px;
                overflow-x: auto;
                overflow-y: hidden;
                overscroll-behavior-inline: contain ;
                z-index: 1;
                &::-webkit-scrollbar {   
                background: #161616;
                border-radius: 10px;
                } 
                &::-webkit-scrollbar-thumb{
                    background-color: #434343;
                    border-radius: 10px;
                    

                }
                
            }
        }
    }
    
</style>