<template>
    <div class="me-fmc" data-scroll-section id="pin" ref="biymc">
        <div class="container">
            <div class="fmc">
                <div class="biy-image">
                    <img class="biy-2" src="@/assets/img/biy-2.jpg"/>
                </div>
                
                <div data-scroll data-scroll-sticky data-scroll-target="#pin" class="fmc-title">
                    <p class="title">Believe in yourself</p>
                </div>
                
                <div class="fmc-secone">
                    <div class="head-one-transition"  style="overflow:hidden;">
                        <p class="head-one">Non-profit Organisation</p>
                    </div>
                    <div class="head-two-transition"  style="overflow:hidden;">
                        <p class="head-two">Website Redesign</p>
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
                    <img class="biy biy-4" src="@/assets/img/biy-4.jpg"/><br>
                    <img class="biy biy-5" src="@/assets/img/biy-5.jpg"/><br>
                    <img class="biy biy-6" src="@/assets/img/biy-6.jpg"/><br>
                    <img class="biy biy-7" src="@/assets/img/biy-7.jpg"/><br>
                    <img class="biy biy-8" src="@/assets/img/biy-8.jpg"/><br>
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

  mounted() {

    this.lmD = new this.locomotiveScroll({
      el: this.$refs.biymc,
      smooth: true,
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
    
  max-width: 80vw;
  margin: 0 auto;

    //border: 2px solid wheat;
    
   .container {
       //display: flex;
        //overflow: auto;
        

        .fmc{
            border: 2px solid white;
            display: grid;
            grid-template-areas: 'title' 'secone' 'gallery';

            .biy-image{
                    position: absolute;
                    top: 0;
                    left: 0;
                    z-index:1;
                .biy-2{
                    
                    width: 100vw;
                    height: auto;
                    
                    //border: 2px solid wheat;
                }
            }

            

            .fmc-title{

                //border: 2px solid white;
                margin-top: 32rem;
                overflow: hidden;
                grid-area: title;
                z-index: 50;
                .title{
                @include ivymode(6.5rem,3.5rem,400);
                //text-transform: uppercase;
                }
            }

            .fmc-secone{
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


            .biy-gallery{
                grid-area: gallery;
                margin: 1rem 0;
                z-index: 2;
                //background-color: white;
                //padding: 0 5rem;
                height: 100%;
                width: 100%;

                .biy-gallery-transition{
                    margin: auto 0;
                }
                .biy{
                    border: 2px solid #fff;
                    width: 100%;
                    margin: 1.4rem 0;
                }
                
            }
        }
    

}

}


</style>
