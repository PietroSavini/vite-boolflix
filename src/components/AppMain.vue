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
            <div class="row mb-3">
                <!-- cards for movies -->
                <div class="ms_card">
                    <img src="" alt="">
                </div>
            </div>
            <h2>TV-Series</h2>
            <div class="row mb-3">
                

            </div>
        </div>
    </section>
</template>

<style scoped lang="scss">
    section{
        height: 50%;
        padding: 2rem 2rem;
    }   
    .jumbotron{
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
            .row{
                height: 150px;
                overflow-x: auto;
                .ms_card{
                    max-width: 342px;
                    padding: 0;
                }
            }
        }
    }
    
</style>