
<template>
    <div class="me-roller" data-scroll data-scroll-section id="pin" ref="roller">

        <div data-scroll data-scroll-sticky data-scroll-target="#pin" class="roller-title" style="">
                    <p class="title">Canada Roller Derby</p>
        </div>
        <div class="container"  id="container">
                <div class="roller-gallery">
                    <div class="roller-gallery-transition m-t-auto m-b-auto m-l-4 m-r-4" v-for="pic in gallery" :key="pic.id" 
                     style="overflow:hidden;" :style="'z-index:'+Math.floor(Math.random() * 10)">
                        <img :class="pic.className" :src="require('@/assets/img/roller/'+pic.id+'.png')" 
                        :style="'height:'+pic.height+'vh;'"/>
                    </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      lmD: null,

      gallery : [
        {id:1 ,className:"roller roller-1", ds_speed:"0.2", height:'64', zIndex:'/works/fmc', m:'m-l-12', n:1, color:'#000'},
        {id:2 ,className:"roller roller-2", ds_speed:"0.2", height:'50', zIndex:'/works/fmc', m:'m-l-12', n:1, color:'#000'},
        {id:3 ,className:"roller roller-3", ds_speed:"0.2", height:'60', zIndex:'/works/fmc', m:'m-l-12', n:1, color:'#000'},
        {id:4 ,className:"roller roller-4", ds_speed:"0.3", height:'54', zIndex:'/works/as', m:'m-l-12', n:2, color:'#C80000'},
		{id:5 ,className:"roller roller-5", ds_speed:"0.4", height:'64', zIndex:'/works/biy', m:'m-l-12', n:3, color:'#C80000'},
		{id:6 ,className:"roller roller-6", ds_speed:"0.5", height:'58', zIndex:'/works/ggym', m:'m-l-12', n:4, color:'#14151c'},
        {id:7 ,className:"roller roller-7", ds_speed:"0.6", height:'50', zIndex:'/works/roller-derby', m:'m-l-12', n:5, color:'#F7FAEE'},
        {id:8 ,className:"roller roller-8", ds_speed:"0.7", height:'64', zIndex:'/works/qg', m:'m-l-12', n:6, color:'#C80000'},
    ],

    };
  },
  mounted() {

    
    
   /* const lastEl = document.getElementsByClassName("roller-8")[0];
    console.log(document.getElementsByClassName("roller-8")[0].getBoundingClientRect().width);
    document.getElementById("container").style.width=
    ((lastEl.getBoundingClientRect().left + lastEl.getBoundingClientRect().width))
    +"px";*/

  },

}
</script>

<style lang="scss" scoped>

.me-roller{

    margin: 0 ;
    width: 100%;
    //color: #000;
    display: flex;
    height: 100vh;

     @include breakpoint(phone) { width: 84vw !important; height:100%; margin: auto;display: grid;grid-template-columns: auto; }

//border: 2px solid red;

    .roller-title{
        mix-blend-mode: difference;
        
        //mix-blend-mode: exclusion;
        //filter: invert(1);
        color: #F7FAEE;
        overflow: hidden;
        padding: 0 0.5rem;
        position: fixed;
        top: 40vh;
        left: 8vw;
        z-index: 5;
        @include breakpoint(phone) { position: relative; left:0; top:12vh; }
        .title{
        @include ivymode(4rem,0rem,400);
        text-transform: uppercase;
        }
    }


    

    
   .container {
       
   
        //display: flex;
        //overflow: auto;
        margin: auto 0;
        width: 100%;
        height: 100%;
//border: 2px solid burlywood;
        
            

           
            .roller-gallery{
                
                //background-color: red;
                //padding: 0 5rem;
                height: 100%;
                position: relative;
                left: 8vw;
                display: flex;
                
                @include breakpoint(phone) { left:0; top:16vh; width:100%;display: grid;grid-template-columns: auto; }
                .roller-gallery-transition:first-child{
                    margin-left:0 ;z-index: 10 !important;
                }
                .roller-gallery-transition{
                    //min-width: 100% !important ;
                    //border: chartreuse 2px solid;
                    @include breakpoint(phone) { margin: 2rem 0 !important ;} 
                }
                .roller{
                    width: auto;
                    @include breakpoint(phone) { width: 100% !important;height: auto !important;}  
                }
            }

}

}


</style>
