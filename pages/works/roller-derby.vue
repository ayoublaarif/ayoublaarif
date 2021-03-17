<template>
<div data-scroll-container ref="meroller" id="roller" class="roller-m">
  <RollerDerby />
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
      tr: null,
      dr: "",
      mqq:"",
      lmS:null,
      arr: [1,2,3,4,5,6,7,8],
      renderComponent:true,
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
        const arr = [1,2,3,4,5,6,7,8];
        arr.forEach(element => {
         this.tr.set( 
         
          el.querySelector(".roller-"+element), {
            y:"125%",
            

        })
        
        });
        console.log("before", this.tr);
       
    },
    enter(el){
    
      console.log("enter", this.tr);

        this.tr
        
        .to(el.querySelector(".title"), {
            y:"0",

        },0)
        const arr = [1,2,3,4,5,6,7,8];
       arr.forEach(element => {
         this.tr.to( 
         
          el.querySelector(".roller-"+element), {
            y:"0",

        }
        ,0.6)
        //console.log(element);
          });
        

        

        
    },
    beforeLeave(el){
        console.log("Leaving, ", el);
        this.tr.to(el.querySelector(".bg-t"), {
          height: "100%",

        })
    },
  },

  mounted(){
    if(this.$mq=="lg"){
            this.dr="horizontal";
    }else{
            this.dr="vertical";
    }
      this.initLScroll(this.dr);
          
      

      console.log(this.lmS)

  },

  watch: {
        '$mq'() {
          if(this.$mq=="sm"){
            this.dr="vertical";
            console.log(this.$mq+"mqq changed vertical"+this.dr);
          }else{
            this.dr="horizontal";
            console.log(this.$mq+"mqq changed horizontal"+this.dr);
          }
          this.lmS.destroy();


          console.log(this.lmS);
          this.initLScroll(this.dr);
          console.log(this.lmS);
        }
  },

 /* watch: {
        '$screen.width'() {
          if(this.$screen.width<=600){
            this.mqq = "phone";
          }else{
            this.mqq = "desktop";
          }
        },
        'mqq'() {
          if(this.mqq==="phone"){
            this.lmS.destroy();
            this.initLScroll(this.dr);
            console.log("mqq changed vertical",this.dr);
          }else{
            this.lmS.destroy();
            this.initLScroll(this.dr);
            console.log("mqq changed horizontal",this.dr);
          }
        },*/




  destroyed(){
    this.lmS.destroy();
    
  },

  methods:{
    initLScroll(d){
      this.lmS = new this.locomotiveScroll({
      el: this.$refs.meroller,
      smooth: true,
      smoothMobile: true,
      direction: d,
      gestureDirection: d,
      getDirection:true,
      lerp: 0.05,
    });
    //this.lmS.init();
    },

    forceRerender() {
  // Remove my-component from the DOM
  this.renderComponent = false;

  // If you like promises better you can
  // also use nextTick this way
  this.$nextTick().then(() => {
    // Add the component back in
    this.renderComponent = true;
  });
}
  }



}
 
</script>

<style lang="scss" scoped>
.roller-m{
  //border: 2px solid blue;
  margin: 0;
  padding: 0;
  background-color: #000;
  color: #fff;
  //height: 300vh;
  width: 600vw;
  height: 100vh !important;
  overflow: hidden;
  @include breakpoint(phone) { width: 100vw;height: 100% !important; overflow: none; }  
}

</style>
