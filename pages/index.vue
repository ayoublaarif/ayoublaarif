<template>
  <div data-scroll-container ref="app" class="app">
    <div class="bg"></div>
    <div ref="bgt" class="bg-t" id="bgt"></div>
  <main id="main">
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
    beforeLeave(el){   
      console.log("Element: ", el);      
      this.tr = this.$gsap.timeline({
            defaults: {duration: 0.5, ease: 'expo'}
        });



        this.tr
       /* .set(el.querySelector(".bg-t"), 
        {backgroundColor: "#EA5830"}
        )*/
        .to(el.querySelector(".bg-t"), {
          height: "100%",

        })
    },
  },

  methods:{
    getColor(color){
      console.log("Onnnn, ", this.bc);
      this.$refs.bgt.style.backgroundColor = color;
    }
  },

   /* transition: {
    name: 'custom',
    mode: 'in-out',
    appear: true,
    css: true,
    duration: { enter: "0ms", leave: "1000ms" },
    beforeEnter(el){
      //this.listWorks = [...el.querySelectorAll(".p")];
      //console.log("We're entering", this.listWorks[0]);
      var i=0;
      for(i=0;i<6;i++){
        this.$gsap.set(el.querySelector(".p"+i), {
        })
      }
       
    },
    afterEnter(el){
      
      
    },
    beforeLeave(el){
      
      //var i=0;for(i=0;i<6;i++){}
        this.$gsap.to(el.querySelector(".bg-t"), {
          duration: 1,
          height: "100%",
          ease:"expo"
            //x: '145%',
        })
        this.$gsap.to(el.querySelector("#main"), {
          duration: 1,
          y: "-15%",
          opacity: 0
            //x: '145%',
        })
      
      console.log("We're leaving", el.querySelectorAll(".p"))
    },
    leave(el){
      
    }
  },*/
  components: { Services, Works, HomeHero },
  
  
  mounted() {
    //this.$refs.bgt.style.backgroundColor = this.bc;
console.log(document.getElementById("bgt").getBoundingClientRect().height)
 

console.log("Color, ", this.bgcolor);
    this.lmSi = new this.locomotiveScroll({
      el: this.$refs.app,
      smooth: true
    });

    this.lmSi.scrollTo("#main");
   
   /*this.lmS = new this.locomotiveScroll({
      el: this.$refs.app,
      smooth: true
    });
  console.log("Mounted");
  

    /* 
    const scroll = new LocomotiveScroll({
      el: this.$refs.app,
      smooth: true,
      smoothMobile: true,
    })*/
  },
  destroyed(){
    this.lmSi.destroy();
 console.log("Counted");
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
.bg{
        position: absolute;
        width: 100vw;
        height: 100%;
        z-index: -100;
        background: $bgColor 0% 0% no-repeat;
        opacity: 1;
        filter: blur(50px);
        -webkit-filter: blur(50px) contrast(0%) opacity(12%);
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
       
/*
.page-enter-active, .page-leave-active {
  transition-duration: $t-duration * 2;
  transition-property: transform,background-color;
  
  
}

.page-leave-active {
  .bg-t{
    transform:scaleY(100%);
  }
}
.page-enter-active,
.page-leave-active {
  transition-duration: $t-duration * 2;
  transition-property: transform,background-color;
  
  
}
.page-leave-active {
  .me-works .p1{
    transform: rotate(20deg);
    background-color: orange;
  }
}*/
</style>
