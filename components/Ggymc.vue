
<template>
  <div class="me-ggym" data-scroll data-scroll-section id="pin" ref="ggym">
    <div class="container">
      <div class="ggym-content">
        <div
          data-scroll
          data-scroll-sticky
          data-scroll-target="#pin"
          class="ggym-title"
          style=""
        >
          <p class="title">GGym Workout Store</p>
        </div>

        <div class="ggym-image">
          <img class="ggym-0" src="@/assets/img/ggym/0.png" />
        </div>

        <div class="ggym-secone">
          <div class="head-one-transition" style="overflow: hidden">
            <p class="head-one">Website Design</p>
          </div>
          <div class="head-two-transition" style="overflow: hidden">
            <p class="head-two">Workout Equipmenet</p>
          </div>

          <div class="description-transition" style="overflow: hidden">
            <p class="description">
              The believe in yourself project promotes <br />
              a postive body image among young women <br />
              and provides charitable donattions of dresses <br />
              to under privileged girls for school dances <br />
              and special occasions.
            </p>
          </div>
        </div>
        <div class="ggym-gallery">
          <div class="ggym-gallery-transition" style="overflow: hidden">
            <img class="ggym ggym-1" src="@/assets/img/ggym/1.png" />
          </div>
          <img class="ggym ggym-2" src="@/assets/img/ggym/2.png" />
          <img class="ggym ggym-3" src="@/assets/img/ggym/3.png" />
          <img class="ggym ggym-4" src="@/assets/img/ggym/4.png" />
          <img class="ggym ggym-5" src="@/assets/img/ggym/5.png" />
          <img class="ggym ggym-6" src="@/assets/img/ggym/6.png" />
          <img class="ggym ggym-7" src="@/assets/img/ggym/7.png" />
          <img class="ggym ggym-8" src="@/assets/img/ggym/8.png" />
          <img class="ggym ggym-9" src="@/assets/img/ggym/9.png" />
          <img class="ggym ggym-10" src="@/assets/img/ggym/10.png" />
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
      direct: "",
    };
  },
  /**/mounted() {
    

    

    if (this.$screen.width <= 768) {
      this.direct = "vertical";
    } else {
      this.direct = "horizontal";
    }console.log(this.direct);
    
    this.initScroll(this.direct);

  },

  watch: {
        '$screen.width'() {
            if(this.$screen.width<=768){
               this.direct = "vertical";
               this.lmD.destroy();
               this.initScroll(this.direct);
               console.log("updated----",this.direct);
            }if(this.$screen.width>768){
                   this.direct = "horizontal";
                   this.lmD.destroy();
                   this.initScroll(this.direct);
                   console.log("updated++++",this.direct);
                  }
        }
    },

    methods: {
        initScroll(direct) {
            this.lmD = new this.locomotiveScroll({
            el: this.$refs.ggym,
            smooth: true,
            direction: direct,
            lerp: 0.05,
            });
        }
    },
    
  destroyed() {
    this.lmD.destroy();
    console.log("Counted");
  },
};
</script>

<style lang="scss" scoped>
.me-ggym {
  margin: 0;
  width: 800vw;

  @media only screen and (max-width: 768px) {
      
      position: relative;
      justify-self: center;
    max-width: 90vw;
    height: 100%;
    margin: 0 auto;
  }
  .container {
    .ggym-content {
      display: flex;
      height: 100vh;

      @media only screen and (max-width: 768px) {
//border: 4px solid navajowhite;
        display: grid;
        grid-template-areas: "title" "secone" "gallery";
        height: 100%;
      }
      .ggym-title {
        @media only screen and (max-width: 768px) {
          color: #ff5900;
          margin-top: 28rem;
          overflow: hidden;
          position: unset;
          grid-area: title;
          z-index: 50;
        }
        mix-blend-mode: difference;
        //border: 2px solid white;
        color: #ff5900;
        overflow: hidden;
        padding: 0 0.5rem;
        position: fixed;
        top: 40vh;
        left: 6vw;
        z-index: 5;
        .title {
          @include ivymode(6.5rem, 2.5rem, 400);
          //text-transform: uppercase;
        }
      }

      .ggym-image {
        @media only screen and (max-width: 768px) {
          position: absolute;
          top: 0;
          left: 0;
          z-index: 1;
        }

        .ggym-0 {
          
          position: absolute !important;
          left: -6vw;
          height: 100vh;
          width: auto;
          z-index: 8;

          @media only screen and (max-width: 768px) {
            width: 100vw;
            height: auto;
            position: unset;
          }
          //border: 2px solid wheat;
        }
      }

      .ggym-secone {
        position: absolute;
        z-index: 2;
        left: 28vw;
        top: 38vh;

        @media only screen and (max-width: 768px) {
          border: 2px solid white;
          grid-area: secone;
          position: unset;
          z-index: 5;
          margin: 2rem 0;
        }
        .head-one {
          @include montserrat(1rem, 0rem, 400);
          margin-bottom: 8.5rem;
          opacity: 0.24;
          @media only screen and (max-width: 768px) {
          margin-bottom: 1rem;
        }
        }

        .head-two {
          @include montserrat(2.4rem, 1rem, 500);
        }
        .description {
          @include montserrat(1rem, 0rem, 400);
          margin: 1rem 0.5rem;
          max-width: 370px !important;
        }
      }

      .ggym-gallery {
        //background-color: white;
        //padding: 0 5rem;
        height: 100%;
        position: absolute;
        left: 75vw;
        display: flex;
        @media only screen and (max-width: 768px) {
          position: unset;
          display: unset;
          grid-area: gallery;
          margin: 1rem 0;
          z-index: 2;
          //background-color: white;
          //padding: 0 5rem;
          height: 100%;
          width: 100%;
        }

        .ggym-gallery-transition {
          margin: auto 0;
        }
        .ggym {
          width: auto;
          @media only screen and (max-width: 768px) {
            position: unset;
            display: flex;
            width: 100%;
            height: auto;
            margin: 1.4rem 0;
          }
        }

        @media only screen and (min-width: 768px) {
              .ggym-1 {
          height: 65vh;
          margin: auto 6rem;
          z-index: 10;
        }
        .ggym-2 {
          height: 50vh;
          margin: 18rem 6rem auto;
          z-index: 1;
        }
        .ggym-3 {
          height: 60vh;
          margin: auto 6rem;
          z-index: 10;
        }
        .ggym-4 {
          height: 40vh;
          margin: 10rem 6rem auto;
          z-index: 1;
        }
        .ggym-5 {
          height: 50vh;
          margin: auto 6rem;
          z-index: 10;
        }
        .ggym-6 {
          height: 60vh;
          margin: auto 6rem;
          z-index: 10;
        }
        .ggym-7 {
          height: 45vh;
          margin: auto 6rem;
          z-index: 1;
        }
        .ggym-8 {
          height: 50vh;
          margin: auto 6rem;
          z-index: 1;
        }
        .ggym-9 {
          height: 40vh;
          margin: auto 6rem;
          z-index: 10;
        }
        .ggym-10 {
          height: 60vh;
          margin: auto 6rem;
          z-index: 10;
        }
          }

      
      }
    }
  }
}
</style>
