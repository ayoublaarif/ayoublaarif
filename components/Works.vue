<template>

  <!-- ... -->

    <div data-scroll-section ref="s3" class="me-works">
        <div  class="container">
            <div class="works">
                   <!-- <p>Follow my club</p>
                    <p>Agdali School</p>
                    <p>Believe In yourself</p>
                    <p>GoatShop</p> 
                    <p>Quuvo Generator</p> -->
                    <div id="work" ref="work" v-for="work in works" :key="work.className" :class="work.className" 
					 data-scroll 
					v-on:mouseenter="mouseOn(work.id,work.className)" 
					v-on:mouseleave="mouseOff()"

                @click="giveColor(work.color)"
					>
                   <!-- <span class="#C80000" color="#C80000" style="display"></span> -->
						<div ref="reveal" class="hover-reveal">
							<div ref="revealInner" class="hover-reveal__inner">
								 <div ref="revealImage" class="hover-reveal__img" :style="{backgroundImage:  'url(' +require('@/assets/img/'+work.srcUrl+'.jpg') + ')' }"></div>
							<!--	<img class="hover-reveal__img" src="../../assets/img/s31.jpg"/> -->
							</div>
						</div>

                    <NuxtLink class="p"  :to="work.toUrl">
                        <p class="work-number">0{{work.n}}</p>
                        <div class="work-detail">
                            <p class="work-name">{{work.name}}</p>
                            <p class="work-head">{{work.head}}</p>
                        </div>
                        <div class="work-desc">
                            <div class="work-line"></div>
                            <div class="work-desc-child">
                                <p class="work-type">Web Design</p>
                                <p class="work-date">07/2020</p>
                            </div>
                        </div>
                       <!-- <span class="m-l-12 work-name-re">{{work.name.substr(work.name.indexOf(" ") + 1)}}</span> -->

                    </NuxtLink>
                    <!--
                        :class="work.m"
                        <a class="p" :href="work.toUrl">{{work.name}}</a>-->
					</div>
            </div>
        </div>
    </div>
</template>

<script>
import gsap from "gsap";
export default {
    data() {
    return {
      works : [
        {id:0 ,className:"p1", ds_speed:"0.2", name:"Footiale", head:"Follow my club", srcUrl:'s30', toUrl:'/works/fmc', m:'m-l-12', n:1, color:'#000'},
        {id:1 ,className:"p2", ds_speed:"0.3", name:"Agdali", head:"Students Monitoring", srcUrl:'s31', toUrl:'/works/as', m:'m-l-12', n:2, color:'#C80000'},
		{id:2 ,className:"p3", ds_speed:"0.4", name:"Believe--In--Yourself", head:"Donation of dresses", srcUrl:'s32', toUrl:'/works/biy', m:'m-l-12', n:3, color:'#C80000'},
		{id:3 ,className:"p4", ds_speed:"0.5", name:"GGym ", head:"Workout Equipmenet", srcUrl:'s33', toUrl:'/works/ggym', m:'m-l-12', n:4, color:'#14151c'},
        {id:4 ,className:"p5", ds_speed:"0.6", name:"Roller--Derby", head:"Follow my club", srcUrl:'s34', toUrl:'/works/roller-derby', m:'m-l-12', n:5, color:'#fffff'},
        {id:5 ,className:"p6", ds_speed:"0.7", name:"Quuvo--Generator", head:"Automatic videos", srcUrl:'s35', toUrl:'/works/qg', m:'m-l-12', n:6, color:'#C80000'},
    ],
    animatableProperties: {
            // translationX
            tx: {previous: 0, current: 0, amt: 0.08},
            // translationY
            ty: {previous: 0, current: 0, amt: 0.08},
            // Rotation angle
            rotation: {previous: 0, current: 0, amt: 0.05}
		},
	firstRAFCycle: false,
	bounds: {},
	mousepos: {x: 0, y: 0},
	sectionLeft: 0,
	activeImage: "",
	revealInner: null,
    revealImage: null,
    mouseison: false,
    };
    },
    mounted(){

        window.addEventListener('mousemove', ev => {
		this.mousepos.x = ev.clientX;
		this.mousepos.y = ev.clientY;
	});

    this.sectionLeft = this.$refs.s3.getBoundingClientRect().left;
    

    },
    methods: {


    giveColor(color){
        this.$emit('giveColor',color);
    },

    calcBounds(){
		  this.bounds = {
            el: this.$refs.work[0].getBoundingClientRect(),
            reveal: this.$refs.reveal[0].getBoundingClientRect()
        };
	  },


	  mouseOn(modelID,className){
         
            this.activeImage = className;
            
			this.revealInner = this.$refs.revealInner[modelID];
			this.revealImage = this.$refs.revealImage[modelID];
		  	this.showImage(this.activeImage);
            this.firstRAFCycle = true;
            this.loopRender();
            console.log("active image 1: " +this.activeImage)
       
            
		
		
	  },
	  mouseOff(){
		  // stop the render loop animation (rAF)
            this.stopRendering();
            // hide the image element
            this.hideImage();
		
	  },

	  showImage(activeImage){
		gsap.killTweensOf(this.revealInner);
        gsap.killTweensOf(this.revealImage);
        gsap.timeline({
			defaults: {duration: 0.8, ease: 'quint'},
			onStart(){
                gsap.set("."+activeImage+" .p", {zIndex: 5000, color:"#FEDDF4"});
                gsap.set("."+activeImage+ " .hover-reveal", {zIndex:500});
                //gsap.set("."+this.activeImage, {zIndex: 50});
                //gsap.set("."+this.activeImage+" .hover-reveal", {zIndex: -1});
			}
        })
        .to("."+activeImage, {
            //rotation: 10
        }, 0)
		.to("."+activeImage+" .hover-reveal", {
            
            opacity: 1,
            //rotation: 10
        }, 0)
        // animate the image wrap
        .to("."+activeImage+" .hover-reveal__inner", {
            startAt: {x: '-50%', y: '150%', rotation: 10},
            x: '0%',
            y: '0%',
            //rotation: 10
        }, 0)
        // scale animation for both inner & image
        .to("."+activeImage+" .hover-reveal__inner", {
            duration: 1, 
            ease: 'expo',
            startAt: {scale: 0.2},
            scale: 1
        }, 0)
        .to("."+activeImage+" .hover-reveal__img", {
            duration: 1, 
            ease: 'expo',
            startAt: {scale: 1.8},
            scale: 1
        }, 0);
	  },

	  hideImage() {
			// kill any current tweens
			gsap.killTweensOf(this.revealInner);
        	gsap.killTweensOf(this.revealImage);
            gsap.timeline({
                defaults: {duration: 0.8, ease: 'quint'},
                onStart(){
                gsap.set(" .p", {zIndex: 1, color:"#000"});
                gsap.set(" .hover-reveal", {zIndex:-1});
                //gsap.set("."+this.activeImage, {zIndex: 50});
                //gsap.set("."+this.activeImage+" .hover-reveal", {zIndex: -1});
			}
			})
			.to("."+this.activeImage+" .hover-reveal", {
            
            opacity: 0,
            //rotation: 10
        	}, 0)
            .to("."+this.activeImage+" .hover-reveal__inner", {
                scale: 0.8,
                x: '50%',
                y: '-150%',
                //rotation: 0
            },0)
            .to("."+this.activeImage+" .hover-reveal__img", {
                scale: 1.8
            }, 0);
    },

	  loopRender(){
		  if ( !this.requestId ) {
            this.requestId = requestAnimationFrame(() => this.render());
        }
	  },

	  stopRendering(){
 		if ( this.requestId ) {
            cancelAnimationFrame(this.requestId);
            this.requestId = undefined;

        }
	  },

	  render(){
		  this.requestId = undefined;
		  if ( this.firstRAFCycle ) {
            // calculate position/sizes the first time
            this.calcBounds();
		}
        this.animatableProperties.tx.current = Math.abs(this.mousepos.x - this.sectionLeft) - this.bounds.reveal.width/2;
        this.animatableProperties.ty.current = Math.abs(this.mousepos.y - this.bounds.el.top) - this.bounds.reveal.height/2;
		//console.log(this.mousepos.x+" HHHHHH "+this.animatableProperties.tx.current+" HHHHHH "+this.bounds.reveal.x)

		this.animatableProperties.tx.previous = this.firstRAFCycle ? this.animatableProperties.tx.current : this.lerp(this.animatableProperties.tx.previous, this.animatableProperties.tx.current, this.animatableProperties.tx.amt);
        this.animatableProperties.ty.previous = this.firstRAFCycle ? this.animatableProperties.ty.current : this.lerp(this.animatableProperties.ty.previous, this.animatableProperties.ty.current, this.animatableProperties.ty.amt);
		//this.animatableProperties.tx.previous = this.animatableProperties.tx.current ;
        //this.animatableProperties.ty.previous = this.animatableProperties.ty.current ;
		
		gsap.set(".hover-reveal", {
            x: this.animatableProperties.tx.previous,
            y: this.animatableProperties.ty.previous,
        });
        //console.log(".p1 .hover-reveal" +document.querySelector(".p1 .hover-reveal").style.zIndex)

        // loop
        this.firstRAFCycle = false;
        this.loopRender();
	  },
	
	lerp(a,b,n){
		return (1 - n) * a + n * b;
	},
	  

	mouseMove(event){
	
		 
	}
    }
}
</script>

<style lang="scss">

.me-works .hover-reveal {
	position: absolute;
	top: 0;
	left: 0;
	z-index: -1;
	width: 300px;
	height: 420px;
	
	pointer-events: none;
	opacity: 0;
	will-change: transform;
	margin: 0;
}

.me-works .hover-reveal__inner {
	overflow: hidden;
}

.me-works  .hover-reveal__inner,
.me-works  .hover-reveal__img {
	width: 100%;
	height: 100%;
	position: relative;
	will-change: transform;
}

.me-works  .hover-reveal__img {
	
	background-size: cover;
	background-position: 50% 50%;
	transform-origin: 50% 100%;
	padding: 50%;
}

.me-works{
    width: 80vw;
    min-height: 100vmin;
    grid-area: section-three;
    position: relative;
   //border: 2px solid teal;
   .container {
        

        .works{




            overflow: hidden;

            #work{
                //border-top: #000000 solid 1px;
                border-top: #000000 solid 0.1rem;
                //background-color: #000000;
                padding: 2rem 1rem;
                margin: 0 0;

                &:last-child{
                    border-bottom: #000000 solid 0.1rem;
                }

            }
            .p{
                display: flex;
                //text-transform: uppercase;
                //font-family: haigrast;
                text-decoration: none;
                cursor: pointer;
                z-index: 50;
                color: #000 !important;

                .work-number{
                    //border: #000000 2px solid;
                    width: 12%;
                    @include breakpoint(phone) { width: 20%;margin-top: 0.8rem; }
                    
                    @include ivymode(1.2rem,0rem,400);
                    margin-top: 0.2rem;


                }

                .work-detail{
                    width: 64%;
                    @include breakpoint(phone) { width: 75%; }
                    .work-name{
                    //border: #000000 2px solid;
                
                        @include ivymode(2.8rem,0rem,400);
                        line-height: 3rem;
                        margin-bottom: 0.4rem;
                        @include breakpoint(phone) { width: 75%; }
                        //border: teal 1px solid;
                    


                    }

                    .work-head{
                        @include montserrat(1rem,0rem,400);
                        opacity: 0.24;
                        text-transform: none;


                        //font-style: italic;
                        //font-weight: 300;
                    }

                }

                


                .work-desc{

                    width: 24%;
                    display: flex;
                        @include breakpoint(phone) { display: none; }
                    .work-line{
                        border-left: #000000 1px solid;
                        height: 100%;
                        width: 2px;
                        margin-left: 4rem;
                        transform: rotate(12deg);
                        opacity: 1;
                    }
                    .work-desc-child{
                        
                        //border: #000000 1px solid;
                        margin: 1rem 0;
                        margin-left: 2rem;
                        .work-type{
                            @include ivymode(1.2rem,0.2rem,400);
                        }
                        .work-date{
                            @include montserrat(0.8rem,0.2rem,400);
                            opacity: 0.24;
                        } 
                    }
                    

                }
            }

        }
    

}

}


</style>
