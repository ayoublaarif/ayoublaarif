<template>
<div data-scroll-container ref="fmc" id="fmc" class="fmc-m">


<Biymc v-if='fmcm=="sm"'/>
    <Fmcc v-if='fmcm=="lg"'/>
    
    
        

</div>
</template>

<script>
import Fmcc from '@/components/Fmcc.vue';
import Biymc from '@/components/Biymc.vue';

export default {
  /*transition(from,to){
    console.log("We're entering from", to);
  },*/

  components: {Fmcc,Biymc },
  data() {
    return {
      tr: null,
      fmcm:"",
      fmcmclass:""
    };
  },
  transition: {
    name: 'custom',
    mode: 'out-in',
    css: true,
    duration: { enter: "500ms", leave: "500ms" },
    beforeEnter(el){
      this.tr = this.$gsap.timeline({
            defaults: {duration: 1, ease: 'expo'}
        });

        this.tr

        .set(el.querySelector(".title"), {
            y:"100%",
        })
        .set(el.querySelector(".head-one"), {
            y:"100%",
        })
        .set(el.querySelector(".head-two"), {
            y:"100%",
        })
        .set(el.querySelector(".description"), {
            y:"100%",
        })
        .set(el.querySelector(".biy-3"), {
            y:"100%",
        })

        .set(el.querySelector(".biy-2"), {
            opacity:0
        })
        console.log("before", this.tr);
       
    },
    enter(el){

      console.log("enter", this.tr);

        this.tr
        
        .to(el.querySelector(".title"), {
            y:"0",

        },0)
        .to(el.querySelector(".head-one"), {
            y:"0",

        },0)
        .to(el.querySelector(".head-two"), {
            y:"0",

        },0)
        .to(el.querySelector(".description"), {
            y:"0",

        },0)
        .to(el.querySelector(".biy-3"), {
            y:"0",

        },0)

        .to(el.querySelector(".biy-2"), {
            opacity:1

        },"-=0.5")

        
    },
    beforeLeave(el){
        console.log("Leaving, ", el);
        this.tr.to(el.querySelector(".bg-t"), {
          height: "100%",

        })
    },
  },


    created(){
      if(this.$device.isDesktop){
          this.fmcm="lg";
      }else{
          this.fmcm="sm";
      }
       console.log("Size, "+this.fmcm);
  },
  mounted(){
    
  },

  /**/watch: {
        '$screen.width'() {
            this.fmcm=this.$mq;
                  console.log("¡¡¡¡"+this.fmcm);
        }
    },



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
@media (max-width: 768px){
.fmc-m{
   width: 100vw;
    justify-content: center;
    height: 600vh;
    overflow: none;
}

}

</style>
