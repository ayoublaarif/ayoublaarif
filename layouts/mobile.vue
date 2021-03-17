<template>
<div>
    <agdali-m/>
    
    
</div>
</template>

<script>
import AgdaliM from '../components/Mobile/AgdaliM.vue'
export default {
  components: { AgdaliM },
  data(){
    return{

    }
  }
}
</script>

<style lang="scss" scoped>

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
.bbbg{
    z-index: -1;
    position: absolute;
    width: 100vw;
    height: 100vh;
    background-color: blue;
}

:root {
	font-size: 12x;
  scroll-behavior: smooth;
  font-family: Ivy Mode;
  -webkit-font-family: Ivy Mode;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;

}

body {
	margin: 0;
  width: 100vw;
  display: block;
}



/*! locomotive-scroll v4.1.0 | MIT License | https://github.com/locomotivemtl/locomotive-scroll */
html.has-scroll-smooth {
  overflow: hidden; }

html.has-scroll-dragging {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none; }

.has-scroll-smooth body {
  overflow: hidden; }

.has-scroll-smooth [data-scroll-container] {
  min-height: 100vh; }

[data-scroll-direction="horizontal"] [data-scroll-container] {
  white-space: nowrap;
  height: 100vh;
  display: inline-block;
  white-space: nowrap; }

[data-scroll-direction="horizontal"] [data-scroll-section] {
  display: inline-block;
  vertical-align: top;
  white-space: nowrap;
  height: 100%; }

.c-scrollbar {
  position: absolute;
  right: 0;
  top: 0;
  width: 11px;
  height: 100%;
  transform-origin: center right;
  transition: transform 0.3s, opacity 0.3s;
  opacity: 0; }
  .c-scrollbar:hover {
    transform: scaleX(1.45); }
  .c-scrollbar:hover, .has-scroll-scrolling .c-scrollbar, .has-scroll-dragging .c-scrollbar {
    opacity: 1; }
  [data-scroll-direction="horizontal"] .c-scrollbar {
    width: 100%;
    height: 10px;
    top: auto;
    bottom: 0;
    transform: scaleY(1); }
    [data-scroll-direction="horizontal"] .c-scrollbar:hover {
      transform: scaleY(1.3); }

.c-scrollbar_thumb {
  position: absolute;
  top: 0;
  right: 0;
  background-color: black;
  opacity: 0.5;
  width: 7px;
  border-radius: 10px;
  margin: 2px;
  cursor: -webkit-grab;
  cursor: grab; }
  .has-scroll-dragging .c-scrollbar_thumb {
    cursor: -webkit-grabbing;
    cursor: grabbing; }
  [data-scroll-direction="horizontal"] .c-scrollbar_thumb {
    right: auto;
    bottom: 0; }
</style>

