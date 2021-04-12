<template>
<div data-scroll-section class="me-hero">
  
  <div class="eclipse-one"></div>
  <div class="eclipse-two"></div>

  <div data-scroll-section  class="container">
      
        <div class="hero-head">
            <div class="content">
                <div class="face"><img src="@/assets/svg/face.svg" class="face-svg"/></div>
                <div class="ayoub"><p class="ayoub-mask" data-splitting>I'M AYOUB A</p></div>
                <div class="desc">
                    <p class="desc-mask" data-splitting>a Creative Designer</p>
                    <p class="desc-mask" data-splitting>And Vue.js Developer</p>
                    <p class="desc-mask" data-splitting>Based in Rabat</p>
                </div>
            </div>
            <div class="hello"><img src="@/assets/svg/hello.svg" class="hello-svg"/><img src="@/assets/svg/hello-mobile.svg" class="hello-mobile-svg"/></div>
        </div>
      
  </div>
  </div>
</template>

<script>
export default {

    mounted: function(){


    },
    methods: {

        
        
    }
}
</script>

<style lang="scss">



.me-hero{

    //border: teal 3px solid;
    grid-area: sectionOne;
    width: 80vw;
    min-height: 80vh;
    margin-top: -6rem;
    
    .container {
        //border: 2px purple solid;
        margin: 0 auto;
        display: flex;
        
        justify-content: center;
        align-items: center;
        text-align: center;

        
        }

        // $bg: #979797 ;

        
    .hero-head{

        $hv:68vh;
        $wv:60vw;

        
        //border: blue 2px solid;
        height: $hv;
        width: $wv;
        margin: 5rem auto 0;
        display: grid;
        grid-template-areas:
            'hero';
        text-align: center;
        align-items: center;
        @include breakpoint(phone) { 
                height:  75vh;
                width: 80vw;
             }
        

        //top: 6vh;

        .content{
            //margin-top: -20rem ;
            grid-area: hero;
        display: grid;
        grid-template-areas:
            'face'
            'ayoub'
            'desc';
        grid-row-gap: 0rem;
        grid-column-gap: 4rem;
        }


        .face{
            opacity: 0;
            position: relative;
            top: -7rem;
            width: 8.4rem;
            z-index: 80;
//
            margin: 0 auto;
            .face-svg{
                width: 100%;
            }
            
        }

        .ayoub{
            position: relative;
            top: -6rem;
            @include montserrat(1.2rem,0rem,300);
            .ayoub-mask{
                overflow: hidden;
                .word > .char, .whitespace{

                    transform: translateY(100%) rotateX(180deg);
                    //transform: ;
                    
                }
                //opacity: 0;
            }
            
        }

        .desc{
            @include ivymode(3.2rem,0rem,400);
            position: relative;
            top: -5rem;
            .desc-mask{
                overflow: hidden;
                .word > .char, .whitespace{

                    transform: translateY(100%) rotateX(180deg);
                    //transform: ;
                    
                }
                
                //opacity: 0;
            }

            
        }

        .hello{
            //border: black 2px solid;
            opacity: 0;

            

            grid-area: hero;
            position: relative;
            height: $hv;
            width: $wv;
            @include breakpoint(phone) { 
                height:  75vh;
                width: 80vw;
             }

            .hello-svg{
                
                height: 100%;
                width: 100%;
                @include breakpoint(phone) { 
                    display: none;
                }
                
            }
            .hello-mobile-svg{
                display: none;
                height: 100%;
                width: 100%;
                @include breakpoint(phone) { 
                    
                    display: unset;
                }
            }
        }
        
    }
  
} 





@media (max-width: 768px){
.me-hero{

    
    .hero-head{

        
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

  //  display: none;
  position: absolute;
  top: 90px;
  left: 120px;
  width: 460px;
  height: 460px;
  z-index: -500;
  border-radius: 50%;
  background: #44378E 0% 0% no-repeat padding-box;
  opacity: 0.2;
  filter: blur(50px);
}
.eclipse-two{

    display: none;
  position: absolute;
  top: 490px;
  left: 886px;
  width: 354px;
  height: 354px;
  z-index: -500;
  transform: matrix(0.99, -0.12, 0.12, 0.99, 0, 0);
  background: #F5E7DC 0% 0% no-repeat padding-box;
  opacity: 1;
  filter: blur(50px);
}




</style>
