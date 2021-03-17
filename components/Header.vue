<template>
<div data-scroll-section class="me-header m-t-2 m-b-2">
  
    <p>AYOUB</p>

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

<style lang="scss">



.me-header{
    grid-area: header;
        display: flex;
        
        justify-content: center;
        align-items: center;
        text-align: center;
        //border: violet 4px solid;

    p{
        @include ivymode(1.8rem,0rem,400);
        letter-spacing: 0.4rem;
    }

}




</style>
