
<template>
    <div class="me-roller" data-scroll-section id="pin" ref="roller">
        <div class="bg-container">

        </div>
        <div class="container">
            <div class="roller">
                <div data-scroll data-scroll-sticky data-scroll-target="#pin" class="roller-title" style="">
                    <p class="title">Canada Roller Derby</p>
                </div>
                <img class="roller-0" src="@/assets/img/ggym/0.png"/>
                <div class="roller-secone">
                    <div class="head-one-transition"  style="overflow:hidden;">
                        <p class="head-one">Website Reesign</p>
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
                <div class="roller-gallery">
                    <div class="roller-gallery-transition" style="overflow:hidden;">
                        <img class="roller roller-1" src="@/assets/img/roller/1.png"/>
                    </div>
                    <img class="roller roller-2" src="@/assets/img/roller/2.png"/>
                    <img class="roller roller-3" src="@/assets/img/roller/3.png"/>
                    <img class="roller roller-4" src="@/assets/img/roller/4.png"/>
                    <img class="roller roller-5" src="@/assets/img/roller/5.png"/>
                    <img class="roller roller-6" src="@/assets/img/roller/6.png"/>
                    <img class="roller roller-7" src="@/assets/img/roller/7.png"/>
                    <img class="roller roller-8" src="@/assets/img/roller/8.png"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      lmD: null,
    };
  },
  mounted() {

    this.lmD = new this.locomotiveScroll({
      el: this.$refs.roller,
      smooth: true,
      direction: "horizontal",
      lerp: 0.05
    }); 
  },
  destroyed(){
    this.lmD.destroy();
    console.log("Counted");
  }
}
</script>

<style lang="scss" scoped>

body{
    
}
.me-roller{
    
    margin: 0 ;
    width: 800vw;
    

    .bg-container{
        position: absolute;
        width: 100vw;
        height: 100vh;
        background-color: #F7FAEE;
        
    }
    
   .container {
       //display: flex;
        //overflow: auto;
        color: #000;

        .roller{
            display: flex;
            height: 100vh;
            .roller-title{
                mix-blend-mode: difference;
                //border: 2px solid white;
                //mix-blend-mode: exclusion;
                //filter: invert(1);
                color: #F7FAEE;
                overflow: hidden;
                padding: 0 0.5rem;
                position: fixed;
                top: 40vh;
                left: 6vw;
                z-index: 5;
                .title{
                @include ivymode(6.5rem,2.5rem,400);
                //text-transform: uppercase;
                
            }
            }

            .roller-0{
                position: absolute !important;
                left: -6vw;
                height: 100vh;
                width: auto;
                //opacity: 0.4;
                
                z-index:8;
                //border: 2px solid wheat;
            }

            .roller-secone{
                position: absolute;
                z-index: 2;
                left: 28vw;
                top: 38vh;

                .head-one{
                    @include montserrat(1rem,0rem,400);
                    margin-bottom: 8.5rem; 
                    opacity: 0.24;
                }

                .head-two{
                @include montserrat(2.4rem,1rem,500);
                
                }
                .description{
                    @include montserrat(1rem,0rem,400);
                    margin: 1rem 0.5rem;
                    max-width: 370px !important;
                    
                }
            }
            
            


            .roller-gallery{
                //background-color: white;
                //padding: 0 5rem;
                height: 100%;
                position: absolute;
                left: 75vw;
                display: flex;

                .roller-gallery-transition{
                    margin: auto 0;
                }
                .roller{
                    width: auto;
                }
                
                
                .roller-1{
                    border: 6px solid #000;
                    height: 65vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .roller-2{
                    height: 50vh;
                    margin:  18rem 6rem auto;
                    z-index: 1;
                }
                .roller-3{
                    height: 60vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .roller-4{
                    height: 40vh;
                    margin: 10rem 6rem auto;
                    z-index: 1;
                }
                .roller-5{
                    height: 50vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .roller-6{
                    height: 60vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .roller-7{
                    height: 45vh;
                    margin: auto 6rem;
                    z-index: 1;
                }
                .roller-8{
                    height: 50vh;
                    margin: auto 6rem;
                    z-index: 1;
                }
                .roller-9{
                    height: 40vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .roller-10{
                    height: 60vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                
            }
        }
    

}

}


</style>
