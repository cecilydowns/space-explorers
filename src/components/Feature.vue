<template>
  <div class="feature" v-on:click.stop="expand" v-bind:class="this.expanded ? 'expanded' : 'condensed'">
    <div v-if="this.expanded" class="close">X</div>
    <div 
      ref="background"
      class="background"
      v-bind:style="this.expanded ? {  transform: `translate(${this.left}px, ${this.top}px) scale(${this.xScale}, ${this.yScale}`  } : { }"
    >
    </div>
    <div class="icon" ref="icon"
      v-bind:style="this.expanded ? { transform: `translate(${this.iconLeft}px, ${this.iconTop}px) scale(2)` } : { }"
    >
        <img ref="iconimage" v-bind:src="require(`../assets/icon${this.icon}.svg`)" class="icon" />
    </div>
    <div class="heading" ref="heading"
      v-bind:style="this.expanded ? { transform: `translate(${this.headingLeft}px, ${this.headingTop}px) scale(2)`, width: `${this.windowWidth / 2}px` } : { }"
    >
        <h3>{{ this.title }}</h3>
    </div>

    <div class="content">
        {{ this.content }}
    </div>

  </div>
</template>

<script>
export default {
  name: "Feature",
  props: {
    title: String,
    content: String,
    icon: String
  },
  data() {
    return {
      expanded: false,
      left: null,
      top: null,
      xScale: null,
      yScale: null,
      iconTop: null,
      iconLeft: null,
      headingTop: null,
      headingLeft: null,
      windowWidth: null
    };
  },
  methods: {
    expand(event) {
      if (this.expanded === false) {
        this.expanded = true;
        // Getting values we need to display the modal
        this.calculateBackgroundSize();
        this.calculateIconPosition();
        this.calculateHeadingPosition();
        this.windowWidth = window.innerWidth;
        // We're acessing <body> with querySelector here since the body tag is outside of the Vue app,
        // and this seems to be the best way to "freeze" the page when the modal is open.
        document.querySelector("body").classList.add("modal");
      } else {
        this.condense();
      }
    },
    condense(event) {
      this.expanded = false;
      document.querySelector("body").classList.remove("modal");
    },
    calculateBackgroundSize() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.background.getBoundingClientRect();
      // We need to swap positive/negative for the the "top" and "left" values to know what value to give
      // our CSS "transform: translate" to get the background to the edge of the screen. (e.g., -100 becomes 100; 50 becomes -50)
      let reversedTop = top >= 0 ? Math.abs(top) * -1 : Math.abs(top);
      let reversedLeft = left >= 0 ? Math.abs(left) * -1 : Math.abs(left);
      this.top = reversedTop;
      this.left = reversedLeft;
      // Calculating value to give CSS Scale property to get background to fill entire screen
      this.xScale = window.innerWidth / width;
      this.yScale = window.innerHeight / height;
    },
    calculateIconPosition() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.icon.getBoundingClientRect();
      //  Converting positive values to negative and vice versa
      let reversedTop = top >= 0 ? Math.abs(top) * -1 : Math.abs(top);
      let reversedLeft = left >= 0 ? Math.abs(left) * -1 : Math.abs(left);

      // Moving the icon position down from the top of the screen by 200px - this code ensures it will work
      // regardless of page scroll position (e.g. even when icon is starting partially off screen)
      reversedTop >= 200 ? (reversedTop -= 200) : (reversedTop += 200);

      this.iconTop = reversedTop;
      this.iconLeft = reversedLeft - this.$refs.iconimage.offsetLeft + 70; // ignore current margin when positioning, and add 70px padding
    },
    calculateHeadingPosition() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.heading.getBoundingClientRect();
      //  Converting positive values to negative and vice versa
      let reversedTop = top >= 0 ? Math.abs(top) * -1 : Math.abs(top);
      let reversedLeft = left >= 0 ? Math.abs(left) * -1 : Math.abs(left);
      this.headingTop = reversedTop;
      this.headingLeft = reversedLeft;
    }
  }
};
</script>

<style scoped lang="less">
@import url("../variables.less");

/* Outer grid item wrapper */
.feature {
  position: relative;
  box-sizing: border-box;
  width: 31%;
  transition: transform 0.2s;
  text-align: center;

  @media screen and (max-width: 600px) {
    width: 100%;
    flex-shrink: 0;
    margin-bottom: 25px;
  }
}

/* Background styles */
.background {
  position: relative;
  background: rgb(65, 24, 65);
  opacity: 0.5;
  height: 150px;
  -webkit-clip-path: polygon(0 8%, 100% 0%, 100% 92%, 0% 100%);
  clip-path: polygon(0 8%, 100% 0%, 100% 92%, 0% 100%);
  transition: transform 1s, opacity 1s;
  transform-origin: top left;
}

.feature.condensed:hover .background {
  opacity: 0.8;
}

.feature.expanded .background {
  overflow: hidden;
  z-index: 100;
  opacity: 0.95;
  clip-path: none;
  -webkit-clip-path: none;
}

/* Icon styles */
.icon {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  margin: -15px auto;
  height: 65px;
  z-index: 20;
  transition: transform 1s;
}

.feature.expanded .icon {
  z-index: 1000;
}

/* Heading styles */
.heading {
  position: absolute;
  box-sizing: border-box;
  top: 30px;
  z-index: 10;
  padding: 15px;
  width: 100%;
  transition: transform 1s;
  transform-origin: top left;
}

.feature.expanded .heading {
  z-index: 1000;
  text-align: left;
}

h3 {
  font-size: 40px;
  line-height: 0.8;
  font-family: @subhead;
  font-weight: bold;
  color: @yellow;
  @media screen and (max-width: 880px) {
    font-size: 35px;
  }
  @media screen and (max-width: 790px) {
    font-size: 30px;
  }
  @media screen and (max-width: 670px) {
    font-size: 27px;
  }
  @media screen and (max-width: 600px) {
    font-size: 40px;
  }
  @media screen and (max-width: 375px) {
    font-size: 30px;
  }
}

/* Content - fades in on click */
.content {
  visibility: hidden;
  opacity: 0;
  position: fixed;
  top: 200px;
  left: 200px;
  color: #fff;
  text-align: left;
  font-size: 20px;
  margin-right: 100px;
  animation-delay: 0.5s;
  transition: opacity 3s;
}

.expanded .content {
  visibility: visible;
  z-index: 1000;
  opacity: 1;
}

/* Top-right "X" button */
.close {
  position: fixed;
  right: 20px;
  top: 20px;
  font-family: "Luckiest Guy";
  cursor: default;
  z-index: 1000;
  animation: fadein 2s;
  color: #fff;
}

/* Keyframes */
@keyframes fadein {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
    transform: scale(1.5);
  }
}
</style>
