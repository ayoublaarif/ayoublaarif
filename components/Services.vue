<template>
    <div class="me-services">
        <div data-scroll-section class="container">

            <p data-scroll data-scroll-speed="1.5" class="title">Services I can help  <br> you with</p>
            <div  class="services">
                <div  class="firstgrp">
                    <p>Front-end Development</p>
                    <p>Web Design</p>
                    <p>UI Design</p>
                    <p>UX Design</p>
                    <p>UI Animation</p>
                    <p>Front-end Development</p>
                    <p>Web Design</p>
                    <p>UI Design</p>
                    <p>UX Design</p>
                    <p>UI Animation</p>
                </div>
                <div class="secondgrp">
                    <p>Front-end Development</p>
                    <p>Web Design</p>
                    <p>UI Design</p>
                    <p>UX Design</p>
                    <p>UI Animation</p>
                    <p>Front-end Development</p>
                    <p>Web Design</p>
                    <p>UI Design</p>
                    <p>UX Design</p>
                    <p>UI Animation</p>
                </div>
            </div>


            <div data-scroll data-scroll-speed="0.25" class="read-more">
                <p class="title">Maybe you want to know <br> what exactly I do</p>
                <div class="read-more-action">
                    <img src="@/assets/svg/readmore.svg" class="read-more-svg"/>
                    <img src="@/assets/svg/arrow.svg" class="arrow-svg"/>
                </div>
                
            </div>

        </div>
    </div>
</template>

<script>
export default {
    //data-scroll data-scroll-speed="15" data-scroll-direction="horizontal"

    mounted: function(){

        /*const tl = this.$gsap.timeline({
            defaults: {duration: 100, repeat:-1}
        });
        tl
        
        .set(".firstgrp", {
            x: "5%",
            //rotation: 10
        }, 0)
        .set(".secondgrp", {
            x: "-50%",
            //rotation: 10
        }, 0)*/


        
        const tl2 = this.$gsap.timeline({
            defaults: {duration: 20, repeat:-1}
        });
        tl2.to(".read-more-svg", {
            startAt: { rotation: 0},
            rotation: 180
        }, 0)

    /*    const tl = this.$gsap.timeline({
            defaults: {duration: 300, repeat:-1}
        });
        tl
        
        .to(".firstgrp", {
            startAt: {x: "-30%",},
            x: "15%",
            //rotation: 10
        }, 0)
        .to(".secondgrp", {
            startAt: {x: "-50%",},
            x: "5%",
            //rotation: 10
        }, 0)
        const tl2 = this.$gsap.timeline({
            defaults: {duration: 50, repeat:-1}
        });
        tl2.to(".read-more-svg", {
            startAt: { rotation: 0},
            rotation: 180
        }, 0)

        */

    },
    methods: {
        
    }
}
</script>

<style lang="scss">

.me-services{
    width: 80vw;
    min-height: 100vmin;
    grid-area: section-two;
   .container {
        .title{
            @include ivymode(3rem,0rem,400);
        }
        

        .services{
            width: 400vw;
            display: grid;
            grid-template-areas: "firstgrp" "secondgrp";
            @include ivymode(5rem,1rem,400);
            text-transform: uppercase;
            margin: 5rem 0;
            

            p{
                white-space: nowrap;
                margin: 0rem 4rem;
                //border: 2px solid black;
                &:first-child{
                    margin-left: 0;
                }
                &:last-child{
                    margin-right: 0;
                }
            }
            
        }
        .firstgrp{
            grid-area: firstgrp;
            display: flex;
            //margin: 0.4rem -25%;
        }
        .secondgrp{
            grid-area: secondgrp;
            display: flex;
            //margin: 0.4rem -70%;
        }
        .read-more{
            display: flex;
            justify-content: space-between;
            align-items: center;
            .title{
                @include montserrat(1.4rem,0rem,400);
            }
            .read-more-action{
                display: grid;
                grid-template-areas: "action";
                align-items: center;
                width: 112px;
                max-width: 20vw;
                cursor: pointer;
                
                .read-more-svg{
                    grid-area: action;
                    width: 100%;
                    
                }
                .arrow-svg{
                    grid-area: action;
                    margin: 0 auto;
                    max-width: 10vw;
                }
            }
        }

        
       
  
    } 
    

}




</style>
