<template>
<div data-scroll-container ref="fmc" id="fmc" class="fmc-m">
    <Fmcc/>
</div>
</template>

<script>
import Fmcc from '@/components/Fmcc.vue';


export default {
  /*transition(from,to){
    console.log("We're entering from", to);
  },*/

  components: {Fmcc },
  data() {
    return {
      lmD: null,
      tr: null
    };
  },
  transition: {
    name: 'custom',
    mode: 'out-in',
    css: true,
    duration: { enter: "500ms", leave: "500ms" },
    beforeEnter(el){
      

        this.tr.set(el.querySelector(".fmc-secone"), {
            y:"25%",
            opacity:0
        })
       
    },
    enter(el){

        this.tr.to(el.querySelector(".fmc-secone"), {
          duration: 0.5,
            y:"0",
            opacity:1

        })
    },
    beforeLeave(el){
        console.log("Leaving, ", el);
        this.tr.to(el.querySelector(".bg-t"), {
          height: "100%",

        })
    },
  },
  mounted() {

    this.lmD = new this.locomotiveScroll({
      el: this.$refs.fmc,
      smooth: true,
      direction: "horizontal",
      lerp: 0.05
    }); 
   /* this.lmS = new this.locomotiveScroll({
      el: this.$refs.fmc,
      smooth: true,
      direction: "horizontal",
      lerp: 0.05
    });
    
   /* 
   this.lmS = new this.locomotiveScroll({
      el: this.$refs.fmc,
      smooth: true,
      //direction: "horizontal",
      lerp: 0.05
    });
    
   
   this.lmS = new this.locomotiveScroll({
      el: this.$refs.app,
      smooth: true
    });
    
    const scroll = new LocomotiveScroll({
      el: this.$refs.app,
      smooth: true,
      smoothMobile: true,
    })*/
  },
  destroyed(){
    this.lmD.destroy();
    console.log("Counted");
  }


}
 
</script>

<style lang="scss" scoped>
.fmc-m{
  margin: 0;
  padding: 0;
  background-color: #000;
    color: #fff;
    //height: 300vh;
    //width: 100vw;
    height: 100vh;

    
    overflow: hidden;
}
</style>
