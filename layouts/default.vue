<template>
    <Nuxt />
    
</template>

<script>
export default {
  data(){
    return{
      isfirstimpression:true,
    }
  },
  mounted(){
    
  }

}
</script>

<style lang="scss">
/*
@import "~splitting/dist/splitting.css";
@import "~splitting/dist/splitting-cells.css";

html {
  font-family:
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}*/



*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

$min_width: 300px;
$max_width: 1600px;
$min_font: 14px;
$max_font: 18px;
:root {
  font-size: calc(6px + (22 - 6) * ((100vw - 320px) / (1600 - 320)));
  //@include fluid-type($min_width, $max_width, $min_font, $max_font); 
  //calc(4.5px + (26 - 14) * ((100vw - 300px) / (1600 - 300)));
  //scroll-behavior: smooth;
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
  height: 100%;
  display: block;
  
}



@media (max-width: 768px){
	html, body {
		//height: 100%;
    }
    :root {
      
    }
    
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




    /* Recommended styles for Splitting */
.splitting .word,
.splitting .char {
  display: inline-block;
}

/* Psuedo-element chars */
.splitting .char {
  position: relative;
}

/**
 * Populate the psuedo elements with the character to allow for expanded effects
 * Set to `display: none` by default; just add `display: block` when you want
 * to use the psuedo elements
 */
.splitting .char::before,
.splitting .char::after {
  content: attr(data-char);
  position: absolute;
  top: 0;
  left: 0;
  visibility: hidden;
  transition: inherit;
  user-select: none;
}

/* Expanded CSS Variables */

.splitting {
  /* The center word index */
  --word-center: calc((var(--word-total) - 1) / 2);

  /* The center character index */
  --char-center: calc((var(--char-total) - 1) / 2);

  /* The center character index */
  --line-center: calc((var(--line-total) - 1) / 2);
}

.splitting .word {
  /* Pecent (0-1) of the word's position */
  --word-percent: calc(var(--word-index) / var(--word-total));

  /* Pecent (0-1) of the line's position */
  --line-percent: calc(var(--line-index) / var(--line-total));
}

.splitting .char {
  /* Percent (0-1) of the char's position */
  --char-percent: calc(var(--char-index) / var(--char-total));

  /* Offset from center, positive & negative */
  --char-offset: calc(var(--char-index) - var(--char-center));

  /* Absolute distance from center, only positive */
  --distance: calc(
     (var(--char-offset) * var(--char-offset)) / var(--char-center)
  );

  /* Distance from center where -1 is the far left, 0 is center, 1 is far right */
  --distance-sine: calc(var(--char-offset) / var(--char-center));

  /* Distance from center where 1 is far left/far right, 0 is center */
  --distance-percent: calc((var(--distance) / var(--char-center)));
}


.splitting.cells img { width: 100%; display: block; }

@supports ( display: grid ) {
  .splitting.cells {
    position: relative;
    overflow: hidden;
    background-size: cover;
    visibility: hidden;
  }

  .splitting .cell-grid {
    background: inherit;
    position: absolute;
    top: 0; 
    left: 0; 
    width: 100%; 
    height: 100%;
    display: grid;
    grid-template: repeat( var(--row-total), 1fr ) / repeat( var(--col-total), 1fr );
  }

  .splitting .cell {
    background: inherit;
    position: relative;
    overflow: hidden;
  }

  .splitting .cell-inner {
    background: inherit;
    position: absolute;
    visibility: visible;
    /* Size to fit the whole container size */
    width: calc(100% * var(--col-total));
    height: calc(100% * var(--row-total));
    /* Position properly */
    left: calc(-100% * var(--col-index));
    top: calc(-100% * var(--row-index));
  }

  /* Helper variables for advanced effects */
  .splitting .cell {
    --center-x: calc((var(--col-total) - 1) / 2);
    --center-y: calc((var(--row-total) - 1) / 2);

    /* Offset from center, positive & negative */
    --offset-x: calc(var(--col-index) - var(--center-x));
    --offset-y: calc(var(--row-index) - var(--center-y));

    /* Absolute distance from center, only positive */
    --distance-x: calc( (var(--offset-x) * var(--offset-x)) / var(--center-x) );

    /* Absolute distance from center, only positive */
    --distance-y: calc( (var(--offset-y) * var(--offset-y)) / var(--center-y) );
  }
}


</style>

