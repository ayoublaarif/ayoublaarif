<template>
<div data-scroll-section class="me-header m-t-2 m-b-2">
    <div class="content">
  
    <p class="logo">AYOUB</p>
    <div class="header-items">
        <!--<p>Services</p>
        <p class="works">Works</p>
        <p class="about">About</p>-->
        <a class="contact" href="#contact">Contact</a>
    </div>
    </div>

</div>

</template>

<script>
export default {

    mounted: function(){


    },
    methods: {
        
    }
}
</script>

<style lang="scss" scoped>



.me-header{
    //opacity: 0 !important;
    grid-area: header;
    .content{
        position: relative;
        margin-top: -2%;
        opacity: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        text-align: center;
    }
        
        //border: violet 4px solid;

    .logo{
        @include ivymode(1.4rem,0rem,600);
        letter-spacing: -0.2rem;
    }

    .header-items{
        display: flex;
        @include montserrat(0.8rem,0rem,400);
        a{
            text-decoration: none;
            margin: 0 0.4rem;
            color: #000000 !important;
        }
    }

}




</style>
