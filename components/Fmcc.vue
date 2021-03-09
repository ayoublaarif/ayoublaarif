<template>
    <div class="me-fmc" data-scroll-section id="pin" ref="biyc">
        <div class="container">
            <div class="fmc">
                <div data-scroll data-scroll-sticky data-scroll-target="#pin" class="fmc-title">
                    <p class="title">Believe in yourself</p>
                </div>
                <img class="biy-2" src="@/assets/img/biy-2.jpg"/>
                <div class="fmc-secone">
                    <div class="head-one-transition"  style="overflow:hidden;">
                        <p class="head-one">Website Redesign</p>
                    </div>
                    <div class="head-two-transition"  style="overflow:hidden;">
                        <p class="head-two">Non-profit Organisation</p>
                    </div>
                    <div class="description-transition"  style="overflow:hidden;"> 
                    <p class="description">The believe in yourself project promotes <br/> 
                    a postive body image among  young women <br/> 
                    and provides charitable donattions of dresses <br/>
                    to under privileged girls for school dances <br/>
                    and special occasions.</p>
                    </div>
                </div>
                <div class="biy-gallery">
                    <div class="biy-gallery-transition" style="overflow:hidden;">
                        <img class="biy biy-3" src="@/assets/img/biy-3.jpg"/>
                    </div>
                    <img class="biy biy-4" src="@/assets/img/biy-4.jpg"/>
                    <img class="biy biy-5" src="@/assets/img/biy-5.jpg"/>
                    <img class="biy biy-6" src="@/assets/img/biy-6.jpg"/>
                    <img class="biy biy-7" src="@/assets/img/biy-7.jpg"/>
                    <img class="biy biy-8" src="@/assets/img/biy-8.jpg"/>
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
      el: this.$refs.biyc,
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
.me-fmc{
    
    margin: 0 ;
    width: 600vw;
    
    
   .container {
       //display: flex;
        //overflow: auto;
        

        .fmc{
            
            display: flex;
            height: 100vh;
            .fmc-title{
                //border: 2px solid white;
                overflow: hidden;
                padding: 0 0.5rem;
                position: fixed;
                top: 40vh;
                left: 20vw;
                z-index: 5;
                .title{
                @include ivymode(6.5rem,2.5rem,400);
                //text-transform: uppercase;
                
            }
            }

            .biy-2{
                position: absolute !important;
                left: 0;
                height: 100vh;
                width: auto;
                z-index:1;
                //border: 2px solid wheat;
            }

            .fmc-secone{
                position: absolute;
                z-index: 2;
                left: 36vw;
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
            
            


            .biy-gallery{
                //background-color: white;
                //padding: 0 5rem;
                height: 100%;
                position: absolute;
                left: 75vw;
                display: flex;

                .biy-gallery-transition{
                    margin: auto 0;
                }
                .biy{
                    border: 2px solid #fff;
                    width: auto;
                }
                
                .biy-2{
                    height: 70vh;
                    margin: auto 6rem auto 0;
                    z-index: 10;
                    
                }
                .biy-3{
                    height: 65vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .biy-4{
                    height: 50vh;
                    margin:  18rem 6rem auto;
                    z-index: 1;
                }
                .biy-5{
                    height: 60vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .biy-6{
                    height: 40vh;
                    margin: 10rem 6rem auto;
                    z-index: 1;
                }
                .biy-7{
                    height: 50vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                .biy-8{
                    height: 60vh;
                    margin: auto 6rem;
                    z-index: 10;
                }
                
            }
        }
    

}

}


</style>
