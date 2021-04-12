<template>
    <div class="me--biy_comp" >
        <div class="biy">
            <div data-scroll data-scroll-sticky data-scroll-target="#me--biy" class="biy-title">
                <p class="title">Believe In Yourself</p>
            </div>

            <div class="content">
                <div class="biy-gallery" ref="gallery">
                    <div  data-scroll class="biy-gallery-transition biy-first m-l-4" style="overflow:hidden;z-index:10;">
                        <img class="biy-g biy-1" src="@/assets/img/biy-3.jpg" style="height:65vh"/>
                    </div>
                    <div data-scroll class="biy-gallery-transition m-t-auto m-b-auto m-l-4 m-r-4" v-for="pic in biyGallery" :key="pic.id" 
                     style="overflow:none;" :style="'z-index:'+Math.floor(Math.random() * 10)" ref="lastPic">

                        <img :class="'biy biy-'+(pic.id+2)" :src="require('@/assets/img/biy-'+(pic.id+2)+'.jpg')" 
                        :style="'height:'+(Math.floor(Math.random() * (65 - 50) + 50))+'vh;'"/>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{

            biyGallery: [
                {id:2, ds_speed:"0.2", height:'64',},
                {id:3, ds_speed:"0.2", height:'64',},
                {id:4, ds_speed:"0.2", height:'64',},
                {id:5, ds_speed:"0.2", height:'64',},
                {id:6, ds_speed:"0.2", height:'64',},
            ]

        }
    },

    mounted(){
        
        this.getGalleryWidth();

    },

    methods:{

        getGalleryWidth(){
            this.$refs.gallery.style.width=((this.$refs.gallery.getBoundingClientRect().right / this.$screen.width) * 100) + 100 + "vw"
            if(process.client){
                console.log(this.$refs.gallery.style.width);
                console.log(this.$screen.width);
                console.log(this.$mq);
            }   
        }


    }

}
</script>

<style lang="scss" scoped>

.me--biy_comp{
    
    .biy{
        display: flex;
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
            .biy-gallery{
                
                height: 100vh;
                overflow: hidden;
                display: flex;
                align-items: center;
                
                //background-color: red;

                .biy-g{
                    height: 75vh;

                }
            }

            

        }
    }
}

</style>