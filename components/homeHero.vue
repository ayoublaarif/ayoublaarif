<template>
<div data-scroll-section class="me-hero">
  
  <div class="eclipse-one"></div>
  <div class="eclipse-two"></div>

  <div data-scroll-section  class="container">
      
        <div class="hero-head">
            <div class="content">
                <div class="face"><img src="@/assets/svg/face.svg" class="face-svg"/></div>
                <div class="ayoub"><p class="ayoub-mask">I'M AYOUB A</p></div>
                <div class="desc"><p class="desc-mask">a Creative Designer<br>
                And Vue.js Developer<br>
                Based in Rabat</p></div>
            </div>
            <div class="hello"><img src="@/assets/svg/hello.svg" class="hello-svg"/></div>
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

<style lang="scss" scoped>



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

        @include ivymode(5rem,3rem,400);
        //border: blue 2px solid;
        height: 75vh;
        width: 64vw;
        margin: 5rem auto 0;

        text-align: center;
        align-items: center;
        display: grid;
        grid-template-areas:
            'face'
            'ayoub'
            'desc';
        grid-row-gap: 0rem;
        grid-column-gap: 4rem;

        //top: 6vh;

        .content{
            //margin-top: -20rem ;
        }


        .face{
            position: relative;
            top: -8rem;
            width: 14rem;
            z-index: 80;
//
            margin: 0 auto;
            .face-svg{
                width: 100%;
            }
            
        }

        .ayoub{
            position: relative;
            top: -8rem;
            @include montserrat(1.4rem,0rem,300);
            
        }

        .desc{
            position: relative;
            top: -6rem;

            
        }

        .hello{
            //border: black 2px solid;
            position: absolute;
            height:  75vh;
            width: 64vw;
            @media (max-width: 768px){
                display: none;

            }

            .hello-svg{
                height: 100%;
                width: 100%;
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
