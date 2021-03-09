<template>
<div data-scroll-container ref="roller" id="roller" class="roller-m">
  <RollerDerby/>
</div>
</template>

<script>
import RollerDerby from '@/components/rollerDerby.vue';


export default {
  /*transition(from,to){
    console.log("We're entering from", to);
  },*/

  components: {RollerDerby },
  data() {
    return {
      tr: null
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
        .set(el.querySelector(".roller-1"), {
            y:"100%",
        })

        .set(el.querySelector(".roller-0"), {
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
        .to(el.querySelector(".roller-1"), {
            y:"0",

        },0)

        .to(el.querySelector(".roller-0"), {
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



}
 
</script>

<style lang="scss" scoped>
.roller-m{
  margin: 0;
  padding: 0;
  background-color: #000;
    color: #fff;
    //height: 300vh;
    //width: 100vw;
    
}
@media (max-width: 768px){
.roller-m{
    height: 100%;
    overflow: none;
}

}

</style>
