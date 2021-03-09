
<template>
    <div class="me-ggym" data-scroll-section id="pin" ref="ggymmc">
        <div class="container">
            <div class="ggym">

                <div class="ggym-image">
                    <img class="ggym-0" src="@/assets/img/ggym/0.png"/>
                </div>

                <div data-scroll data-scroll-sticky data-scroll-target="#pin" class="ggym-title" style="">
                    <p class="title">GGym Store</p>
                </div>
                <div class="ggym-secone">
                    <div class="head-one-transition"  style="overflow:hidden;">
                        <p class="head-one">Website Design</p>
                    </div>
                    <div class="head-two-transition"  style="overflow:hidden;">
                        <p class="head-two">Workout Equipmenet</p>
                    </div>
                    
                    <div class="description-transition"  style="overflow:hidden;"> 
                    <p class="description">The believe in yourself project promotes <br/> 
                    a postive body image among  young women <br/> 
                    and provides charitable donattions of dresses <br/>
                    to under privileged girls for school dances <br/>
                    and special occasions.</p>
                    </div>
                </div>
                <div class="ggym-gallery">
                    <div class="ggym-gallery-transition" style="overflow:hidden;">
                        <img class="ggym ggym-1" src="@/assets/img/ggym/1.png"/>
                    </div>
                    <img class="ggym ggym-2" src="@/assets/img/ggym/2.png"/>
                    <img class="ggym ggym-3" src="@/assets/img/ggym/3.png"/>
                    <img class="ggym ggym-4" src="@/assets/img/ggym/4.png"/>
                    <img class="ggym ggym-5" src="@/assets/img/ggym/5.png"/>
                    <img class="ggym ggym-6" src="@/assets/img/ggym/6.png"/>
                    <img class="ggym ggym-7" src="@/assets/img/ggym/7.png"/>
                    <img class="ggym ggym-8" src="@/assets/img/ggym/8.png"/>
                    <img class="ggym ggym-9" src="@/assets/img/ggym/9.png"/>
                    <img class="ggym ggym-10" src="@/assets/img/ggym/10.png"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
data(){
    return{
        lmD: null,
    }
},


}
</script>

<style lang="scss" scoped>

body{
    
}
.me-ggym{
    
  max-width: 80vw;
  margin: 0 auto;


    border: 8px solid wheat;
    
   .container {
       //display: flex;
        //overflow: auto;
        

        .ggym{
            display: grid;
            grid-template-areas: 'title' 'secone' 'gallery';

            .ggym-image{
                    position: absolute;
                    top: 0;
                    left: 0;
                    z-index:1;
                .ggym-0{
                    
                    width: 100vw;
                    height: auto;
                    
                    //border: 2px solid wheat;
                }
            }

            

            .ggym-title{

                //border: 2px solid white;
                color: #ff5900;
                margin-top: 32rem;
                overflow: hidden;
                grid-area: title;
                z-index: 50;
                .title{
                @include ivymode(6.5rem,3.5rem,400);
                //text-transform: uppercase;
                }
            }

            .ggym-secone{
                grid-area: secone;
                z-index: 5;
                margin: 2rem 0;
            }
            
            .head-one,.head-two{
                @include montserrat(2.4rem,1rem,400);
                
            }
            .description{
                @include montserrat(1rem,0rem,400);
                margin: 1rem 0rem;
                max-width: 370px !important;
                
            }


            .ggym-gallery{
                grid-area: gallery;
                margin: 1rem 0;
                z-index: 2;
                //background-color: white;
                //padding: 0 5rem;
                height: 100%;
                width: 100%;

                .ggym-gallery-transition{
                    margin: auto 0;
                }
                .ggym{
                    width: 100%;
                    margin: 1.4rem 0;
                }
                
            }
        }
    

}

}


</style>
