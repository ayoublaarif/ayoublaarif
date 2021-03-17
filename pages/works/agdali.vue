<template>
<main>
    <h1>current: {{$mq}}</h1>
</main>
</template>

<script>
import AgdaliD from '../../components/Desktop/AgdaliD.vue';
import AgdaliM from '../../components/Mobile/AgdaliM.vue';
import { MatchMedia } from "vue-component-media-queries";

export default {
    //  layout: (ctx) => ctx.$device.isMobile ? 'mobile' : 'desktop',

    components: { MatchMedia, AgdaliD, AgdaliM },
    
}
</script>

<style lang="scss" scoped>

</style>