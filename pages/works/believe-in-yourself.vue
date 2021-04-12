<template>
        <div class="me-biy" id="me--biy" data-scroll-container ref="mebiy">
           <div class="content" id="content"  data-scroll-section>
              <div data-scroll data-scroll-sticky data-scroll-target="#content" class="biy-title">
                <p class="title">Believe In Yourself</p>
              </div>


              <div data-scroll class="biy-gallery-transition m-t-auto m-b-auto m-l-4 m-r-4" v-for="pic in biyGallery" :key="pic.id" ref="tran"
                style="" :style="pic.id != 1 ? 'z-index:'+Math.floor(Math.random() * 10)+
                ';--ht:'+(Math.floor(Math.random() * (65 - 50) + 50))+'vh;height:var(--ht);' : 'z-index:10;height:65vh'" 
                >

                  <img :class="'biy biy-'+(pic.id+2)" :src="require('@/assets/img/biy-'+(pic.id+2)+'.jpg')" 
                  style='height:100%;width:auto'
                  :ref="pic.id == 6 ? 'lastPic' : ''"/>

              </div>


              <div data-scroll class="invisible"></div>
           </div>
            <!--<div class="bg-t"></div> 747 height is 500-->
        </div>
</template>


<script>
import BelieveInYourself from '@/components/BelieveInYourself.vue';


export default {
  /*transition(from,to){
    console.log("We're entering from", to);
  },*/

  components: {BelieveInYourself},
  data() {
    return {
      tr: null,
      dr: "",
      mqq:"",
      lmSb:null,
      biyGallery: [
                {id:1, ds_speed:"0.2", height:'64',},
                {id:2, ds_speed:"0.2", height:'64',},
                {id:3, ds_speed:"0.2", height:'64',},
                {id:4, ds_speed:"0.2", height:'64',},
                {id:5, ds_speed:"0.2", height:'64',},
                {id:6, ds_speed:"0.2", height:'64',},
            ]
    };
  },
  transition: {
    
  },

  beforeMount(){
    console.log("width is ",this.$refs.tran);
  },

 

  mounted(){
    

const tl = this.$gsap.timeline({
            onComplete:this.completedd,
            defaults: {duration: 0.5, ease: 'Power3.easeOut'},
      })
      .to('.biy-gallery', { opacity: 0.2 },0);

      
    /*  

    if(this.$mq=="lg"){
            this.dr="horizontal";
    }else{
            this.dr="vertical";
    }
    console.log(this.lmSb)
    //this.initLScroll();
    console.log(this.lmSb)*/
    

    //
    //const locomotive = this.$refs.scroller.locomotive

    /*this.lmSi = new this.locomotiveScroll({
              el: this.$refs.mebiy,
              smooth: true,
              direction:"horizontal"

    });*/
    

  },

   methods:{
    completedd(){
      this.getGalleryWidth();
      console.log("Completed baby");
      //this.initLScroll();
      
    },
    getGalleryWidth(){
      //console.log("width is ",window.getComputedStyle(this.$refs.mebiy,null).getPropertyValue("width"));
      this.$refs.mebiy.style.width=((this.$refs.lastPic[0].getBoundingClientRect().right / this.$screen.width) * 100) + 100 + "vw"
      console.log("width is "+this.$refs.tran[1].offsetWidth+" height is "+this.$refs.tran[1].offsetHeight);
            if(process.client){
                
            }   
        },
    initLScroll(){
      this.lmSb = new this.locomotiveScroll({
      el: this.$refs.mebiy,
      smooth: true,
      direction: "horizontal",
      smartphone:{
        smooth: true,
        direction: "horizontal",
      },
      tablet:{
        smooth: true,
        direction: "horizontal",
      },
      //lerp: 0.05,
    });

    this.lmSb.init();
  },
  intro(){
    const tl = this.$gsap.timeline({
            onComplete:this.completedd,
            defaults: {duration: 0.5, ease: 'Power3.easeOut'},
      })
      .to('.biy-gallery', { opacity: 0.2 },0);
  }


},

  watch: {
        '$screen.width'() {
            console.log(this.$mq+"mqq changed vertical");
            this.lmSb.destroy();
            this.initLScroll();
            this.lmSb.update();
        }
  },
  
  destroyed(){ 

    
    
  },




}
 
</script>

<style lang="scss" scoped>
.me-biy{
  
  //border: 2px solid blue;
  //background-color: #000000 !important;


  background-color: red;
  color: #ffffff;
  overflow-y: hidden;
  overflow-x: none;
  width: 100vw;
  height: 100vh;
  @include breakpoint(phone) {
    display: grid;grid-template-columns: auto;
    overflow-y: none;
    overflow-x: hidden;
    
    }
  //white-space: nowrap;


    .biy-title{
            mix-blend-mode: difference;
            
            //mix-blend-mode: exclusion;
            //filter: invert(1);padding: 0 0.5rem;
            
            position: fixed;
            top: 40vh;
            left: 8vw;
            /* ++++++++++++++++++ Problem de return to the first left: 8vw ++++++++++++++++++ */


            z-index: 5;
            //white-space: nowrap;
            @include breakpoint(phone) { position: relative; left:0; top:12vh; }
            .title{
            @include ivymode(5rem,0rem,400);
            text-transform: uppercase;
            }
        }
    .content{
      
        background: #000000;
        display: flex;
        height: 100vh;
        overflow: hidden;
        //margin: auto 0;

        .biy-gallery-transition{
          border: 2px red solid;
          overflow-x:none !important;
          overflow-y: none;
          

          img{
            //margin-left: -5rem;
          }
        }
        .invisible{
          min-width: 90vw;
          //  border: blue 2px solid;
        }

        @include breakpoint(phone) {display: grid;grid-template-columns: auto; height: unset; width: 100vw;}

        }

  //display: flex;

  //@include breakpoint(phone) { width: 100vw; height: 100% !important; overflow: none; }  
}

</style>
