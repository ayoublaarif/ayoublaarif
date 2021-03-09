<template>
<div data-scroll-container ref="ggym" id="ggym" class="ggym-m">
 <Ggymc/>
</div>
</template>

<script>
import Ggymc from '@/components/Ggymc.vue';
import Ggymmc from '@/components/Ggymmc.vue';


export default {
  /*
  <client-only>
 <Ggymc v-if="this.$screen.width>765" />
   <Ggymmc  v-if="this.$screen.width<=765" />
   </client-only>
  transition(from,to){
    console.log("We're entering from", to);
  },*/

  components: {Ggymc, Ggymmc },
  data() {
    return {
      tr: null,
      ishow: false,
      renderComponent:true,
      componentKey: 0,
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
        .set(el.querySelector(".ggym-1"), {
            y:"100%",
        })

        .set(el.querySelector(".ggym-0"), {
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
        .to(el.querySelector(".ggym-1"), {
            y:"0",

        },0)

        .to(el.querySelector(".ggym-0"), {
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

  /*computed:{
    media() {
      if(this.$screen.width<=768){
        return this.ishow=true;
      }else
             {
              return this.ishow=false;
            }
    }
    
  },
  watch: {
        '$screen.width'() {
            console.log("When it's false", this.componentKey);

              // If you like promises better you can
              // also use nextTick this way
                this.componentKey += 1;
                console.log("When it's true", this.componentKey);
              

        }
    }*/



}
 
</script>

<style lang="scss" scoped>
.ggym-m{
  margin: 0;
  padding: 0;
  background-color: #14151c;
  color: #fff;
    //height: 300vh;
    //width: 100vw;
    
}
@media (max-width: 768px){
.ggym-m{
  width: 100vw;
  height: auto;
    overflow: none;
        border: 4px solid hotpink;
        padding: 0;
        margin: 0;
}

}

</style>
