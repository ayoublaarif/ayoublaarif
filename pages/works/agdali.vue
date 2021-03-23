<template>
<main >
    <div v-show="isLoaded">
    <h1 ref="cp" class="content__paragraph" data-splitting>current: {{$mq}}</h1>
    <input type="button" value="Test" v-on:click="switched"/>

    <input type="button" value="Reverse" v-on:click="timeline.reverse()"/>
    <img class="picture" @load="onImgLoad" src="@/assets/img/roller/1.png" style='height:50vh;'/>
    </div>
</main>
</template>

<script>
import AgdaliD from '../../components/Desktop/AgdaliD.vue';
import AgdaliM from '../../components/Mobile/AgdaliM.vue';
import { MatchMedia } from "vue-component-media-queries";


export default {
    //  layout: (ctx) => ctx.$device.isMobile ? 'mobile' : 'desktop',

    data(){
        return{
            timeline:null,
            imagesLoaded: 0,
            totalImages: 0,
            isLoaded: false,

            

        }
    },

    components: { MatchMedia, AgdaliD, AgdaliM },
    methods:{
        onImgLoad() {
            console.log(` >> isLoaded:`, this.isLoaded)
            return this.isLoaded = true
        },

        switched(){

            //console.log(this.timeline.restart());
            let content = {
                section: document.querySelector('.content__paragraph'),
                get chars() {
                return this.section.querySelectorAll('.char');
                },
            };



            
            
            console.log("chaaaaars",this.$refs.cp);

            const timelineSettings = {
            staggerValue: 0.1,
            charsDuration: 1
            };var els = document.querySelectorAll('.content__paragraph .word > .char, .whitespace');
             this.timeline = this.$gsap.timeline({paused: false})
                
                //.addLabel('start')
                // Stagger the animation of the home section chars
                
                .staggerTo(".content__paragraph .word > .char, .whitespace", timelineSettings.charsDuration, {
                    ease: 'Power3.easeIn',
                    display: "inline-block",
                    color:  "red",
                    y: "100%"
                }, timelineSettings.staggerValue)

        },



        allImagesLoaded(){
            console.log("All images are loaded");
        }

    },
        mounted(){
            this.Splitting()

            const images = document.querySelectorAll('img')
            
            this.totalImages = images.length;
            images.forEach((image) => {
                

                image.onload = () => {
                    console.log(image);

                this.imagesLoaded++;
                if (this.imagesLoaded == this.totalImages) {
                    this.allImagesLoaded()
                }

                }

            })

            
                
                // Here we do the switch
                // We need to toggle the current class for the content sections
                /*
                .addLabel('switchtime')
                .to(document.querySelectorAll('.content__paragraph'), {
                    y: '150%'
                },'switchtime')
                
                
                .to(document.querySelectorAll('.content__paragraph'), {
                    y: '150%'
                },0)
                .addLabel('switchtime')
                .add( () => {
                    DOM.content.home.section.classList.toggle('content__item--current');
                    DOM.content.about.section.classList.toggle('content__item--current');
                })
                // Change the body's background color
                .to(document.body, {
                    duration: 0.8,
                    ease: 'Power1.easeInOut',
                    backgroundColor: '#c3b996'
                }, 'switchtime-=timelineSettings.charsDuration/4')
                // Start values for the about section elements that will animate in
                .set(DOM.content.about.chars, {
                    y: '100%'
                }, 'switchtime')
                .set(DOM.content.about.picture, {
                    y: '40%',
                    rotation: -4,
                    opacity: 0
                }, 'switchtime')
                // Stagger the animation of the about section chars
                .staggerTo( DOM.content.about.chars, timelineSettings.charsDuration, {
                    ease: 'Power3.easeOut',
                    y: '0%'
                }, timelineSettings.staggerValue, 'switchtime')
                // Finally, animate the picture in
                .to( DOM.content.about.picture, 0.8, {
                    ease: 'Power3.easeOut',
                    y: '0%',
                    opacity: 1,
                    rotation: 0
                }, 'switchtime+=0.6');*/



        
    }
    
}
</script>

<style lang="scss" scoped>
span{
    
}

main{
    position:relative;
  overflow:hidden;
        div{
            margin: auto 0;
            position:relative;
        }
        .content__paragraph{
            span{
                color: green !important;
            }
            
	position: relative;
	overflow: hidden;
	flex: none;
    border: black 2px solid;
        }

        
        justify-content: center;
        align-items: center;
        text-align: center;
        height: 100vh;
        
}

</style>