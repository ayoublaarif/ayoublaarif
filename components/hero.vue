<template>
<div data-scroll-section class="me-hero">
  
  <div class="eclipse-one"></div>
  <div class="eclipse-two"></div>
 <!-- <div class="container">
    <div>
      
        <div class="hero-head">
            <span class="hero-header">Creative Designer</span>
        </div>
        <div class="hero-head"> 
            <span class="hero-header"> & Vue.js Developer </span>
            <span><img src="@/assets/svg/nuxt.svg" class="nuxt-svg" /></span>
            <span class="hero-sup">
                <span>USING</span> 
                <span>NUXT.JS</span>
            </span>
        </div>
        <div class="hero-head">
           <span class="hero-header">Based in </span><span><img src="@/assets/svg/rabat.svg" class="rabat-svg" /></span><span class="hero-header"> Rabat</span>
        </div>
      
    </div>
  </div> -->

  <div data-scroll-section  class="container">
      
        <div class="hero-head">
            <span class="ayoub"><p class="ayoub-mask">I'M AYOUB A</p></span>
            <span data-scroll class="creative"><p class="creative-mask">Creative</p></span>
            <span class="designer"><p class="designer-mask">Designer</p></span>
            <span class="vue"><p class="vue-mask">& Vue.js</p></span>
            <span class="developer"><p class="developer-mask">Developer</p></span>
            <span class="nuxt"> 
                <div class="hero-nuxt">
                    <span><img src="@/assets/svg/nuxt.svg" class="nuxt-svg"/></span>
                    <span class="hero-sup">
                        <span>USING</span> 
                        <span>NUXT.JS</span>
                    </span>
                </div>
            </span>
            <span class="based"><div class="based-inner"><p class="based-mask">Based in</p></div></span>
            <span class="hassan"><img src="@/assets/svg/rabat.svg" class="rabat-svg" /></span>
            <span class="rabat"><div class="rabat-inner"><p class="rabat-mask">Rabat</p></div></span>
            <span class="morocco"><div class="morocco-inner"><p class="morocco-mask">IN MOROCCO</p></div></span>
            
            
        </div>
      
  </div>
  </div>
</template>

<script>
export default {

    mounted: function(){
        const tl = this.$gsap.timeline({
            defaults: {duration: 2, ease: 'expo'}
        });
        tl
        
        .to(".ayoub-mask", {
            startAt: {y: "150%",},
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".creative-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".designer-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".vue-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".developer-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".rabat-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".based-mask", {
            startAt: {y: "150%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".morocco-mask", {
            startAt: {y: "200%", },
            y: 0,
            rotation: 0
            //rotation: 10
        }, 0)
        .to(".hassan", {
            startAt: {scale: 0.4},
            opacity: 1,
            scale: 1
            //rotation: 10
        }, 1)
        .to(".nuxt", {
            startAt: {scale: 0.4},
            opacity: 1,
            scale: 1
            //rotation: 10
        }, 1)
        .to(".eclipse-one", {
            startAt: {scale: 0},
            scale: 1,
            opacity: 0.2
            //rotation: 10
        }, 1)
        .to(".eclipse-two", {
            startAt: {scale: 0},
            scale: 1,
            opacity: 1
            //rotation: 10
        }, 1)
        

    },
    methods: {
        clickedA(){
          const tlw = this.$gsap.timeline({
            defaults: {duration: 4, ease: 'expo'}
        });

        tlw.to(".ayoub-mask", {
            y: "50%",
            opacity: 0.5
            //rotation: 10
        }, 0)  
        console.log("clicked")
        }
        
    }
}
</script>

<style lang="scss" scoped>


/*.me-hero{
    .hero-head{
        display: flex;
        justify-content: center;
        align-items: center;
        //border: black 3px solid;
        .hero-header {
            margin: 0 1rem auto;
            //border: red 3px solid;
            font-size: 7rem;
            font-weight: 400;
        }
        span{
            margin: auto 1rem;
        }
        .hero-sup{
        
        span{
           display: block; 
           text-align: left;
           margin: auto 0rem;
           font-family: Poppins;
           font-weight: 300;
           font-size: 2rem;
            }
            
        }
          .nuxt-svg{
            width: 7rem;
        }
        .rabat-svg{
            width: 3rem;
            margin: 1.5rem 1rem 0;
        }
    }
  
} */ 

.me-hero{
    .container {
        //border: 2px purple solid;
        margin: 0 auto;
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;

        
        }

        // $bg: #979797 ;

        
    .hero-head{

        font-size: 7rem;
        font-weight: 400;
        
        max-width: 100%;
        //text-align: left;
        display: grid;
        grid-template-areas:
            'ayoub ayoub ayoub'
            'creative creative creative'
            'vue vue vue'
            'rabat rabat rabat'
            'morocco morocco morocco';
        grid-row-gap: 0rem;
        grid-column-gap: 2rem;
        .hero-nuxt{ 
            display: flex;
            .hero-sup{
            margin: auto 0 1rem;
            //b
                span{
                    display: block; 
                    text-align: left;
                    margin: auto 0.5rem 0;
                    @include montserrat(1.4rem,0rem,300);
                }
                
            }
        }
        
    }


    .ayoub{
        grid-area: ayoub;
        @include montserrat(1.4rem,0rem,300);
        margin-left: 13rem;
        margin-right: auto;
        margin-bottom: -1rem;
        overflow: hidden;
        
    }
    .ayoub-mask{
        

    }
    .creative{
        //border: red 3px solid;
        overflow: hidden;
        grid-area: creative;
        margin-left: 8rem;
        margin-right: auto;

    }
    .designer{
        overflow: hidden;
        grid-area: creative;
        margin-left: 26rem;
        //border: red 3px solid;
       // position: relative;
       // left: 30rem;
       
    }

    .vue{
        overflow: hidden;
        grid-area: vue;
        margin-right: auto;
    }
    .developer{
        overflow: hidden;
        grid-area: vue;
        margin-left: 26rem;
        margin-right: 16rem;
        //border: red 3px solid;
    }
    .nuxt{
        opacity: 0;
        overflow: hidden;
        grid-area: vue;
        margin-left: auto;
        //border: red 3px solid;
    }

    .based{
        grid-area: rabat;
        margin-left: 10rem;
        margin-right: auto;

        .based-inner{
            overflow: hidden;
        }
    }
    .hassan{
        grid-area: rabat;
        opacity: 0;
        //border: blue 3px solid;
        margin: 0 auto 0 38rem;
        padding: 1.5rem 0 0;
        
        
    }
    .rabat{
        grid-area: rabat;
        text-align: left;
        margin-left: 44rem;
       // border: blue 3px solid;
        .rabat-inner{
            overflow: hidden;
        }
    }

    .morocco{
        overflow: hidden;
        grid-area: morocco;
        text-align: left;
        margin-left: 44rem;
        margin-top: -4rem;
        //border: red 3px solid;
        @include montserrat(1.4rem,0rem,300);
        text-align: left;
        padding-left: 0.4rem;

        .morocco-inner{
            overflow: hidden;
        }
    }


    .nuxt-svg{
            width: 7rem;
        }
        .rabat-svg{
            width: 4rem;
            margin:  0;
        }
  
} 





@media (max-width: 768px){
.me-hero{

    
    .hero-head{
        // border: orchid 2px solid;
        font-size: 4rem;
        max-width: 100%;
        //text-align: left;
        display: grid;
        grid-template-areas:
            'ayoub ayoub ayoub'
            'creative creative creative'
            'designer designer designer'
            'vue nuxt nuxt'
            'developer developer developer'
            'based based hassan'
            'rabat rabat hassan'
            'morocco morocco hassan';
        grid-row-gap: 0rem;
        grid-column-gap: 2rem;
        .hero-nuxt{ 
            
            display: flex;
            .hero-sup{
            margin: auto 0 1rem;
            //b
                span{
                    display: block; 
                    text-align: left;
                    margin: auto 0.5rem 0;
                    font-family: Poppins;
                    font-weight: 300;
                    font-size: 1rem;
                }
                
            }

        }
        
    }


    .ayoub{
        grid-area: ayoub;
        font-family: Poppins;
        font-weight: 300;
        font-size: 1rem;
        margin-bottom: 0;
        margin-right: 0;
        margin-left: auto;
    }
    .creative{
        
        //border: blue 3px solid;
        grid-area: creative;
        margin-right: 0;
        margin-left: auto;

    }
    .designer{
        grid-area: designer;
        margin-right: 0;
        margin-left: auto;
        
    //
       // position: relative;
       // left: 30rem;
       
    }

    .vue{
        grid-area: vue;
        margin-right: -3rem;
        margin-left: auto;
        //border: red 3px solid;
    }
    .developer{
        grid-area: developer;
        margin-right: 0;
        margin-left: auto;
        //border: red 3px solid;
    }
    .nuxt{
        grid-area: nuxt;
        margin-right: 0;
        margin-left: auto;
       // border: red 3px solid;
    }

    .based{
        grid-area: based;
        margin-right: 0;
        margin-left: auto;
        padding: 0;
        
    }
    .hassan{
        grid-area: hassan;
        margin-right: 0;
        margin-left: auto;
        //border: blue 3px solid;
        
        
    }
    .rabat{
        grid-area: rabat;
        margin-right: 0;
        margin-left: auto;
        text-align: right;
    }
    .morocco{
        //border: red 3px solid;
        grid-area: morocco;
        font-family: Poppins;
        font-weight: 300;
        font-size: 1rem;
        text-align: right;
        padding-left: 0.4rem;
        margin-left: auto;
        margin-right: 0;
        margin-top: 0;
    }


    .nuxt-svg{
            width: 4rem;
            margin: 0;
    }
    .rabat-svg{
            width: 4rem;
            margin:  0;
    }
    .eclipse-one{
        position: fixed;
        top: -8rem;
        left: -15rem;
    }
    .eclipse-two{
        position: fixed;
        top: 40rem;
        left: 16rem;
    }
    
}

    


}

.eclipse-one{
  position: absolute;
  top: 90px;
  left: 120px;
  width: 460px;
  height: 460px;
  z-index: -500;
  border-radius: 50%;
  background: #44378E 0% 0% no-repeat padding-box;
  opacity: 0;
  filter: blur(50px);
}
.eclipse-two{
  position: absolute;
  top: 490px;
  left: 886px;
  width: 354px;
  height: 354px;
  z-index: -500;
  transform: matrix(0.99, -0.12, 0.12, 0.99, 0, 0);
  background: #F5E7DC 0% 0% no-repeat padding-box;
  opacity: 0;
  filter: blur(50px);
}




</style>
