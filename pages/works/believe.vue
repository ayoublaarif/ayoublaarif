<template>
        <div v-if="tr" class="me-biy" id="me--biy" data-scroll-container ref="mebiy">
           <div class="content" id="content"  data-scroll-section>
              <div data-scroll data-scroll-sticky data-scroll-target="#content" class="biy-title">
                <p class="title">Believe In Yourself</p>
              </div>


              <div class="biy-gallery-transition" v-for="pic in biyGallery" :key="pic.id" ref="tran"
                :style="$mq != 'sm' ? 'z-index:'+Math.floor(Math.random() * 10)+
                ';width:'+(Math.floor(Math.random() * (60 - 50) + 50))+'vw;' : 'z-index:10;width:100%'" 
                :class="pic.id == 1 ? 'firstPic' : ''">

                  <img :class="'biy biy-'+(pic.id+2)" :src="require('@/assets/img/biy-'+(pic.id+2)+'.jpg')" 
                  :ref="pic.id == 6 ? 'lastPic' : ''"/>

              </div>


              <div class="invisible">{{$mq == 'sm' ? 'width:100%' : 'height:var(--ht);'}}</div>
           </div>
            <!--<div class="bg-t"></div> 747 height is 500-->
        </div>
</template>


<script>
import BelieveInYourself from '@/components/BelieveInYourself.vue';


export default {

components: {BelieveInYourself},
  data() {
    return {
      tr: true,
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

    mounted(){
        console.log(this.$mq);
        if(this.$mq!="sm"){
            this.initLScroll();
            console.log("The first initialized",this.lmSb);

          }
    },

    watch: {
        '$mq'() {
          if(this.$mq!="sm"){
            this.initLScroll();
            console.log("it's initialized 77777");
          }else{
              if(this.lmSb!=null) { this.lmSb.stop();this.lmSb.destroy();this.lmSb=false;this.tr=false;this.tr=true;console.log("it's destroyed 77777",this.lmSb);}
            
          }
        }
    },


}
 
</script>

<style lang="scss" scoped>
.me-biy{
  
    height: 100vh;
    display: flex;
    overflow: hidden;
    background-color: black;
    color: #fff;
  @include breakpoint(phone) {

    
    display: grid;grid-template-columns: auto;
    overflow-y: none;
    overflow-x: hidden;
    max-width: 100vw;
    height: 100%;
    
    
    }


    .biy-title{
            mix-blend-mode: difference;
            //border: 2px red solid;
            //mix-blend-mode: exclusion;
            //filter: invert(1);padding: 0 0.5rem;
            
            position: fixed;
            top: 40vh;
            left: 8vw;
            /* ++++++++++++++++++ Problem de return to the first left: 8vw ++++++++++++++++++ */


            z-index: 5;
            //white-space: nowrap;
            @include breakpoint(phone) { position: relative; top:0; left:0; }
            .title{
            @include ivymode(5rem,0rem,400);
            text-transform: uppercase;
            }
        }
    .content{

        display: flex;
        background: #000000;
        align-items: center;
        @include breakpoint(phone) {
            //position: relative;top: 50rem;
            max-width: 90vw;
            display: grid;
            grid-template-columns: auto;
            height: unset; 
            overflow-x: hidden;
            margin: 0 auto;
            }

        .firstPic{
            width: 62vw !important;
            z-index: 10 !important;
            
            }
        .biy-gallery-transition{
          overflow: none;
          margin: 0 4rem;
          //border: 8px red solid;
          @include breakpoint(phone) { margin: 2rem 0; }
          img{
            width: 100%;
            //@include breakpoint(phone) { width: 100%; }
            
          }
        }
        .invisible{
          min-width: 90vw;
          @include breakpoint(phone) { min-height: 90vh; }
          //  border: blue 2px solid;
        }

        

        }

  //display: flex;

  //@include breakpoint(phone) { width: 100vw; height: 100% !important; overflow: none; }  
}

</style>
