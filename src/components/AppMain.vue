<script>
import { store } from '../store';
import AppCardMovie from "./AppCardMovie.vue";
import AppCardTv from "./AppCardTv.vue"
export default {
    data(){
        return{
            store,
        }
    },
    components:{
        AppCardMovie,
        AppCardTv,
    },

}

</script>

<template>
    <section class="jumbotron">
        <div class="container jumbo">
            <div class="row">
                <div v-if="store.movies && store.series !== [] && store.movies[store.active]" class="col-4">
                    <ul v-if="store.type === 'movie'"  class="details mt-3">
                        <li><h2 class="jumbo-title">{{ store.movies[store.active].title }}</h2></li>
                        <li><h3 class="jumbo-original-title mb-4">{{store.movies[store.active].original_title}}</h3>
                            <span class="lang m-2">({{ store.movies[store.active].original_language }})</span>
                            <span class="rating">{{ store.movies[store.active].vote_average }}</span>
                        </li>
                        <li><p class="jumbo-description">{{ store.movies[store.active].overview }}</p></li>
                    </ul>
                    <ul v-if="store.type==='tv'" class="details mt-3">
                        <li><h2 class="jumbo-title">{{ store.series[store.active].name}}</h2></li>
                        <li><h3 class="jumbo-original-title mb-4">{{store.series[store.active].original_name}}</h3>
                            <span class="lang m-2">({{ store.series[store.active].original_language }})</span>
                            <span class="rating">{{ store.series[store.active].vote_average }}</span>
                        </li>
                        <li><p class="jumbo-description">{{ store.series[store.active].overview }}</p></li> 
                    </ul>
                    
                    
                    
                    
                   
                </div>
                <div v-if="store.movies && store.series !== [] && store.movies[store.active]" class="col-8">
                    <img v-if="store.type === 'movie'" :src="`${store.jumboImgUrl}${store.movies[store.active].backdrop_path}`" alt="">
                    <img v-if="store.type === 'tv'" :src="`${store.jumboImgUrl}${store.series[store.active].backdrop_path}`" alt="">
                    <div class="overlay"></div> 
                </div>
                
            </div>
        </div>
    </section>
    
    <section class="results">
        
        <div class="container">
            <h2>Movies</h2>
            <div class="row media-scroller mb-3 flex-nowrap align-items-center">
                <!-- cards for movies -->
                <AppCardMovie @click="store.active=index, store.type='movie'" v-for="(movieCard,index) in store.movies" :movie="movieCard"/>
            </div>
            <h2>TV-Series</h2>
            <div class="row media-scroller flex-nowrap align-items-center mb-3">
                <AppCardTv @click="store.active=index, store.type='tv'" v-for="(tvCard,index) in store.series" :tv="tvCard"/>

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
        min-height: 400px;
        max-height: 700px;
        .jumbo{
            height: 100%;
            .row{
                height: 100%;
            }
            .col-4{
                position: relative;
                color: #fff;
                height: 100%;
                &::-webkit-scrollbar {
                    width: 0px;
                }
                ul{
                    position: absolute;
                    width: 200%;
                    left: 50px;
                    z-index: 4;
                    list-style-type: none;
                    height: 100%;
                    overflow-x: auto;
                    &::-webkit-scrollbar {   
                        width: 0; 
                    } 


                    .jumbo-original-title{
                        font-size: 1rem;
                        display: inline-block;
                    }
                    .jumbo-description{
                            font-size: .7rem;
                            max-width: 50%;
                    }
                }
            }
            .col-8{
                position: relative;
                padding: 0 0;
                z-index: 2;
                height: 100%;
                img{
                    object-fit: cover;
                    width: 100%;
                    height: 100%;
                }
                .overlay{
                    position: absolute;
                    top: 0;
                    height: 100%;
                    width: 100%;
                    z-index: 3;
                    border: 1px solid black;
                    background-image: linear-gradient( to right, rgba(0,0,0, 1 ) 10%,rgba(0, 0, 0, 0) 60%, );
                    box-shadow: inset 0px 0px 20px black;
                }

            }
        }  
    }
    
    .results{
        flex-grow: 1;
        height: 65%;
        padding-bottom: 0;
        z-index: 1;
        box-shadow: inset 0px 0px 20px black;
        background: linear-gradient( rgb(0,0,0)20%,rgba(19, 18, 18,) ) ;
       
        
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