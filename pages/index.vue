<template>
  <div data-scroll-container ref="app" class="app app-scroll" id="me-app">
    <div class="bg"></div>
    <div ref="bgt" class="bg-t" id="bgt"></div>
  <main id="main" ref="main" class="completed">
    <Header/>
    <HomeHero/>
    <Services/>
    <Works v-on:giveColor="getColor"/>
    </main>
</div>
</template>

<script>
import Hero from '@/components/hero'
import Services from '@/components/Services.vue'
import Works from '@/components/Works.vue'
import HomeHero from '@/components/homeHero.vue'
import { ScrollTrigger } from 'gsap/ScrollTrigger'



export default {

  data() {
    return {
      lmSi: null,
      tr: null,
      bc: "#000",
    };
  },
    transition: {
    name: 'custom',
    mode: 'out-in',
    css: true,
    duration: { enter: "500ms", leave: "500ms" },
    beforeEnter(el){   
      
      //this.animateBefore(el);
      
      
    },


    enter(el){

    },


    beforeLeave(el){        
      this.tr = this.$gsap.timeline({
            defaults: {duration: 0.5, ease: 'expo'}
        })
        .to(el.querySelector(".bg-t"), {
          height: "100%",

        })
    },
  },

  methods:{
    getColor(color){
      this.$refs.bgt.style.backgroundColor = color;
    },

    animateBefore(el){   
      this.tr = this.$gsap.timeline();



        this.tr
        
        .set(el.querySelector(".face"), {
          opacity: 0,

        })
        .set(el.querySelector(".hello"), {
          opacity: 0,

        })
        
       /* .set(el.querySelector(".bg-t"), 
        {backgroundColor: "#EA5830"}
        )*/
        .to(el.querySelector(".bg-t"), {
          height: "0%",

        })
    },

    animateLoad(el){
      const timelineSettings = {
                  staggerValue: 0.015,
                  charsDuration: 0.5
      };
      
      this.Splitting();

      const tl = this.$gsap.timeline({
            onComplete:this.completed,
            defaults: {duration: 0.5, ease: 'Power3.easeOut'},
      })

        .addLabel('start')
        
        .staggerTo('.desc-mask .word > .char, .whitespace', timelineSettings.charsDuration, 
                {
                   
                    y:"0%",
                    rotationX: 0,
                }, 
                timelineSettings.staggerValue, 'start')

        .staggerTo('.ayoub-mask .word > .char, .whitespace', timelineSettings.charsDuration, 
                {
                   
                    y:"0%",
                    rotationX: 0,
                }, 
                timelineSettings.staggerValue, 'start')


          .to('.face', { opacity: 1 },'start+=0.4')
          .to('.hello', { opacity: 1 },'start+=0.4');

           
    },
    completed(){
            document.getElementById("main").classList.toggle('completed');
            this.lmSi.update();
            const tl2 = this.$gsap.timeline({paused:false,
            defaults: {duration: 0.4, ease: 'Power3.easeOut'},
            })
            .to(".me-header .content", { opacity: 1, marginTop:"0%"},0)
            .to(".me-header ", {},0)
            
    },

    initScrolltrigger(lmSi){
      // tell ScrollTrigger to use these proxy methods for the ".smooth-scroll" element since Locomotive Scroll is hijacking things
      ScrollTrigger.scrollerProxy(".app-scroll", {
        scrollTop(value) {
          return arguments.length ? lmSi.scrollTo(value, 0, 0) : lmSi.scroll.instance.scroll.y;
        }, // we don't have to define a scrollLeft because we're only scrolling vertically.
        getBoundingClientRect() {
          return {top: 0, left: 0, width: window.innerWidth, height: window.innerHeight};
        },
        // LocomotiveScroll handles things completely differently on mobile devices - it doesn't even transform the container at all! So to get the correct behavior and avoid jitters, we should pin things with position: fixed on mobile. We sense it by checking to see if there's a transform applied to the container (the LocomotiveScroll-controlled element).
        //pinType: document.querySelector(".app-scroll").style.transform ? "transform" : "fixed"
      });
    },


    elementAnimation() {
      const tl = this.$gsap.timeline({
            defaults: {duration: 8}
        });
        tl
        
        .set(".firstgrp", {
            margin: "0.4rem -28%",
            //rotation: 10
        }, 0)
        .set(".secondgrp", {
            margin: "0.4rem -38%",
            //rotation: 10
        }, 0)
        .to(".firstgrp", {
            margin: "0.4rem -13%",
            //rotation: 10
        }, 0)
        .to(".secondgrp", {
            margin: "0.4rem -53%",
            //rotation: 10
        }, 0)

        ScrollTrigger.create({
          trigger:".me-services",
          start:"top 50%",
          end:"+=1400",
          scroller:".app-scroll",
          animation:tl,
          scrub:true,
          pin:false
        })
    },




  },

  components: { Services, Works, HomeHero },
  beforeMount(){
  },
  
  
  mounted() {
    this.$gsap.registerPlugin(ScrollTrigger);


    
    this.animateLoad(document.getElementById("me-app"));


    this.lmSi = new this.locomotiveScroll({
              el: this.$refs.app,
              smooth: true
    });
    const lmSi = this.lmSi; 

    this.lmSi.scrollTo("#main");



    // each time Locomotive Scroll updates, tell ScrollTrigger to update too (sync positioning)
    this.lmSi.on("scroll", ScrollTrigger.update);

    const _self = this;

    this.initScrolltrigger(lmSi);
    this.elementAnimation();

    


    

      



    // each time the window updates, we should refresh ScrollTrigger and then update LocomotiveScroll. 
    // ScrollTrigger.addEventListener("refresh", () => this.lmSi.update());

    // after everything is set up, refresh() ScrollTrigger and update LocomotiveScroll because padding may have been added for pinning, etc.
    // ScrollTrigger.refresh();

  },
  
  destroyed(){
    this.lmSi.destroy();
  }



}
 
</script>

<style lang="scss">
$t-duration: 800ms;



:root{
  --bgco: #EA5830;
  
}

$bgc:#000;
.app{
  
  width: 100vw;
  height: 100%;
  overflow: hidden;

}
.completed{
  height: 100vh;
}
main{
  max-width: 80vw;
  
  margin: 0 auto;
  //border: violet 4px solid;


  display: grid;
  grid-template-areas:
  'header'
  'sectionOne'
  'section-two'
  'section-three';
  grid-row-gap: 4rem;

}

.bg-t{
        position: fixed;
        bottom: 0;
        width: 100vw;
        height: 0%;
        z-index: 800;
        
        background-color: $bgc;
        opacity: 1;
        }
</style>
