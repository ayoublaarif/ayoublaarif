<template>
<main style="position: fixed; left: 0px; right: 0px; top: 0px; bottom: 0px; overflow: hidden; margin: 0; padding: 0;">
    <div class="bg"></div>
   <!-- 
     
     <div v-show="isLoaded">
    <h1 ref="cp" class="content__paragraph" data-splitting>current: {{$mq}}</h1>
    <input type="button" value="Test" v-on:click="switched"/>

    <input type="button" value="Reverse" v-on:click="timeline.reverse()"/>
    <img class="picture" @load="onImgLoad" src="@/assets/img/roller/1.png" style='height:50vh;'/>
    </div> -->

    <canvas 
    id="canvas"
    style="width: 100%; height: 100%; padding: 0;margin: 0;"
  ></canvas>
  
  <div class="container" ref="contact">
      <Contact/>
  </div>

  
</main>
</template>

<script>
import AgdaliD from '../../components/Desktop/AgdaliD.vue';
import AgdaliM from '../../components/Mobile/AgdaliM.vue';
import { MatchMedia } from "vue-component-media-queries";
import Contact from '@/components/Contact.vue'


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

    components: { Contact, AgdaliD, AgdaliM },
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
        },


        canvabg(){

            const canvas = document.getElementById("canvas");
    const c = canvas.getContext("2d");

    // size of canvas
    const imgSize = 512;

    canvas.width = imgSize;
    canvas.height = imgSize;

    // init image data with black pixels
    const image = c.createImageData(imgSize, imgSize);
    for (let i = 0; i < image.data.length; i += 4) {
      image.data[i] = 0; // R
      image.data[i + 1] = 0; // G
      image.data[i + 2] = 0; // B
      image.data[i + 3] = 255; // A
    }

    // size of our height maps
    const mapSize = 1024;

    // returns the distance of point x,y from the origin 0,0
    const distance = (x, y) => Math.sqrt(x * x + y * y);

    // init height map 1
    const heightMap1 = [];
    for (let u = 0; u < mapSize; u++) {
      for (let v = 0; v < mapSize; v++) {
        // index of coordinate in height map array
        const i = u * mapSize + v;

        // u,v are coordinates with origin at upper left corner
        // cx and cy are coordinates with origin at the
        // center of the map
        const cx = u - mapSize / 2;
        const cy = v - mapSize / 2;

        // distance from middle of map
        const d = distance(cx, cy);

        // stretching so we get the desired ripple density on our map
        const stretch = (3 * Math.PI) / (mapSize / 2);

        // wavy height value between -1 and 1
        const ripple = Math.sin(d * stretch);

        // wavy height value normalized to 0..1
        const normalized = (ripple + 1) / 2;

        // height map value 0..128, integer
        heightMap1[i] = Math.floor(normalized * 128);
      }
    }

    const heightMap2 = [];
    for (let u = 0; u < mapSize; u++) {
      for (let v = 0; v < mapSize; v++) {
        const i = u * mapSize + v;
        const cx = u - mapSize / 2;
        const cy = v - mapSize / 2;

        // skewed distance as input to chaos field calculation,
        // scaled for smoothness over map distance
        const d1 = distance(0.8 * cx, 1.3 * cy) * 0.022;
        const d2 = distance(1.35 * cx, 0.45 * cy) * 0.022;

        const s = Math.sin(d1);
        const c = Math.cos(d2);
        // height value between -2 and +2
        const h = s + c;

        // height value between 0..1
        const normalized = (h + 2) / 4;
        // height value between 0..127, integer
        heightMap2[i] = Math.floor(normalized * 127);
      }
    }

    // color helpers

    const interpolate = (c1, c2, f) => {
      return {
        r: Math.floor(c1.r + (c2.r - c1.r) * f),
        g: Math.floor(c1.g + (c2.g - c1.g) * f),
        b: Math.floor(c1.b + (c2.b - c1.b) * f)
      };
    };

    // returns a random color
    const randomColor = () => {
      const r = Math.floor(Math.random() * 255);
      const g = Math.floor(Math.random() * 255);
      const b = Math.floor(Math.random() * 255);
      return { r, g, b };
    };

    // returns a random color palette with 256 color entries
    /*const makeRandomPalette = () => {
      const c1 = {r:15,g:12,b:41};
      const c2 = {r:48,g:33,b:99};
      const c3 = {r:36,g:36,b:62};
      const c4 = {r:48,g:33,b:99};
      const c5 = {r:15,g:12,b:41};

      return makeFiveColorGradient(c1, c2, c3, c4, c5);
    };

    const makeFiveColorGradient = (c1, c2, c3, c4, c5) => {
      const g = [];

      for (let i = 0; i < 64; i++) {
        const f = i / 64;
        g[i] = interpolate(c1, c2, f);
      }

      for (let i = 64; i < 128; i++) {
        const f = (i - 64) / 64;
        g[i] = interpolate(c2, c3, f);
      }

      for (let i = 128; i < 192; i++) {
        const f = (i - 128) / 64;
        g[i] = interpolate(c3, c4, f);
      }

      for (let i = 192; i < 256; i++) {
        const f = (i - 192) / 64;
        g[i] = interpolate(c4, c5, f);
      }

      return g;
    };*/

    // offsets for moving height maps
    let dx1 = 0;
    let dy1 = 0;

    let dx2 = 0;
    let dy2 = 0;

    // adjust height maps offsets
    const moveHeightMaps = t => {
      dx1 = Math.floor(
        (((Math.cos(t * 0.0002 + 0.4 + Math.PI) + 1) / 2) * mapSize) / 2
      );
      dy1 = Math.floor((((Math.cos(t * 0.0003 - 0.1) + 1) / 2) * mapSize) / 2);
      dx2 = Math.floor((((Math.cos(t * -0.0002 + 1.2) + 1) / 2) * mapSize) / 2);
      dy2 = Math.floor(
        (((Math.cos(t * -0.0003 - 0.8 + Math.PI) + 1) / 2) * mapSize) / 2
      );
    };

    const linearGradient = (c1, c2) => {
    const g = [];
    // interpolate between the colors in the gradient
    for (let i = 0; i < 256; i++) {
        const f = i / 255;
        g[i] = interpolate(c1, c2, f);
    }
    return g;
    };
    // current palette is edstablished durting animation
        let palette = []
    // two palettes we interpolate between
    const palettes = [linearGradient(
            { r: 68, g: 55, b: 142 },
            { r: 255, g: 255, b: 255 },
        ), linearGradient(
            { r: 254, g: 221, b: 244 },
            { r: 255, g: 255, b: 255 },
        )];

    

    // stores whether we're interpolating colors
    // from palette 0 -> 1 (1) or 1 -> 0 (-1)
    let prevDirection = 1;

    const updatePalette = t => {
      const timeScale = 0.0005;
      const x = t * timeScale;

      // normalized value 0..1 used to interpolate palette colors
      const inter = (Math.cos(x) + 1) / 2;

      // did we switch direction, and should ergo pick a new palette
      // random palette to interpolate towards?

      const direction = -Math.sin(x) >= 0 ? 1 : -1;
      if (prevDirection != direction) {
        prevDirection = direction;
        if (direction == -1) {
          palettes[0] = linearGradient(
            { r: 68, g: 55, b: 142 },
            { r: 255, g: 255, b: 255 },
        );
        } else {
          palettes[1] = linearGradient(
            { r: 254, g: 221, b: 244 },
            { r: 255, g: 255, b: 255 },
        );
        }
      }

      // create interpolated palette for current frame
      for (let i = 0; i < 256; i++) {
        palette[i] = interpolate(palettes[0][i], palettes[1][i], inter);
      }
    };

    const updateImageData = () => {
      for (let u = 0; u < imgSize; u++) {
        for (let v = 0; v < imgSize; v++) {
          // indexes into height maps for pixel
          const i = (u + dy1) * mapSize + (v + dx1);
          const k = (u + dy2) * mapSize + (v + dx2);

          // index for pixel in image data
          // remember it's 4 bytes per pixel
          const j = u * imgSize * 4 + v * 4;

          // height value of 0..255
          let h = heightMap1[i] + heightMap2[k];
          // get color value from current palette
          let c = palette[h];

          // h = heightMap2[i];
          // c = { r: h, g: h, b: h };

          // set pixel data
          image.data[j] = c.r;
          image.data[j + 1] = c.g;
          image.data[j + 2] = c.b;
        }
      }
    };

    // helper to create a linear gradient palette
    /*const linearGradient = (c1, c2) => {
      const g = [];

      // interpolate between the colors
      // in the gradient

      for (let i = 0; i < 256; i++) {
        const f = i / 255;
        g[i] = interpolate(c1, c2, f);
      }

      return g;
    };*/

    const tick = time => {
      moveHeightMaps(time);
      updatePalette(time);
      updateImageData();

      c.putImageData(image, 0, 0);

      requestAnimationFrame(tick);
    };

    requestAnimationFrame(tick);
            
        }

    },
        mounted(){

          console.log("width is ",window.getComputedStyle(this.$refs.contact,null).getPropertyValue("width"));

            this.canvabg();
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
    //background:linear-gradient(270deg,#161315 0,rgba(22,19,21,0));
    //background: #161315 ;
    /*position:relative;
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
        }*/

        
        justify-content: center;
        align-items: center;
        text-align: center;
        height: 100vh;


        .bg{
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: #000000 !important;
            opacity: 1 !important;
            border: black 50px solid;
            //filter: blur(50px) contrast(0px) opacity(0.12);
            //-webkit-filter: blur(50px) contrast(0px) opacity(12px);
            //opacity: 0;
            z-index: 5000;
        }

        canvas{
            z-index: -4;
            position: absolute;
            top: 0;
            left: 0;
        }

        .container{
            max-width: 80vw;
            margin: auto;
            //border: #fff 2px solid;
            display: flex;
            padding-top: 6% ;
        }
        
}

</style>