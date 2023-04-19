<script>
export default {
    data(){
        return{

        }
    }
}
</script>

<template>
    <section class="jumbotron">
        <div class="container jumbo">
            <div class="row">
                <div class="col-4"></div>
                <div class="col-8"></div>
            </div>
        </div>
    </section>
    
    <section class="results">
        
        <div class="container">
            <h2>Movies</h2>
            <div class="row">
                <!-- cards for movies -->
                <div class="col">
                    
                </div>
            </div>
            <h2>TV-Series</h2>
            <div class="row">
                

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
        }  
    }
    
    .results{
        overflow-y: auto;
        z-index: 1;
        box-shadow: inset 0px 0px 20px black;
        background: linear-gradient( rgb(0,0,0)10%,rgb(19, 18, 18) ) ;
        &::-webkit-scrollbar {
            width: 0px;    
        }
        
        .container{
            height: 100%;
            color: #fff;
            .row{
                height: 50%;
                overflow-x: auto;
            }
        }
    }
    
</style>