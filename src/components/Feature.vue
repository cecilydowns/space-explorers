<template>
    <div class="feature" v-on:click.stop="expand" v-bind:class="this.expanded ? '' : 'condensed'">
      <div 
        ref="background"
        v-bind:class="this.expanded ? 'inner inner-expanded' : 'inner'"
        v-bind:style="this.expanded ? {  transform: `translate(${this.left}px, ${this.top}px) scale(${this.xScale}, ${this.yScale}`  } : { }"
      >
      </div>
          <div class="icon" ref="icon"
              v-bind:class="this.expanded ? 'expanded' : ''"
              v-bind:style="this.expanded ? { transform: `translate(${this.iconLeft}px, ${this.iconTop}px) scale(2)` } : { }">
              <img v-bind:src="require(`../assets/icon${this.icon}.svg`)" class="icon" />
          </div>

          <div class="heading" ref="heading"
              v-bind:class="this.expanded ? 'expanded' : ''"
              v-bind:style="this.expanded ? { transform: `translate(${this.headingLeft}px, ${this.headingTop}px) scale(2)` } : { }">
              <h3>{{ this.title }}</h3>
          </div>

          <div
            v-bind:style="this.expanded ? { transform: `translate(${this.textLeft}px, ${this.textTop}px)`, width: `${this.textWidth}px` } : { width: `100%`}"
            v-bind:class="this.expanded ? 'text expanded' : 'text'"
            ref="text">
              <p>{{ this.content }} </p>
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
      iconXScale: null,
      iconYScale: null,
      headingTop: null,
      headingLeft: null,
      textTop: null,
      textLeft: null,
      textWidth: null,
      textWidthSmall: null
    };
  },
  mounted() {
    this.$nextTick(function() {
      window.addEventListener("resize", this.calculateModalSize);
    });
  },
  methods: {
    expand(event) {
      console.log("IN EXPAND");
      if (this.expanded === false) {
        this.expanded = true;
        this.calculateModalSize();
        this.calculateIconSize();
        this.calculateHeadingPosition();
        this.calculateTextPosition();
        document.querySelector("body").classList.add("modal");
      } else {
        this.condense();
      }
    },
    condense(event) {
      this.expanded = false;
      document.querySelector("body").classList.remove("modal");
    },
    calculateModalSize() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.background.getBoundingClientRect();
      let reversedTop = top >= 0 ? Math.abs(top) * -1 : Math.abs(top);
      let reversedLeft = left >= 0 ? Math.abs(left) * -1 : Math.abs(left);
      this.top = reversedTop;
      this.left = reversedLeft;
      this.xScale = window.innerWidth / width;
      this.yScale = window.innerHeight / height;
      // this.inverseXScale = 1 / this.xScale;
      // this.inverseYScale = 1 / this.yScale;
    },
    calculateIconSize() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.icon.getBoundingClientRect();
      let reversedTop = top >= 0 ? Math.abs(top - 50) * -1 : Math.abs(top + 50);
      let reversedLeft =
        left >= 0 ? Math.abs(left - 50) * -1 : Math.abs(left + 50);
      this.iconTop = reversedTop;
      this.iconLeft = reversedLeft;

      console.log("icontop", this.iconTop);
      console.log("iconleft", this.iconLeft);
    },
    calculateHeadingPosition() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.heading.getBoundingClientRect();
      let reversedTop =
        top >= 0 ? Math.abs(top - 120) * -1 : Math.abs(top + 120);
      let reversedLeft =
        left >= 0 ? Math.abs(left - 50) * -1 : Math.abs(left + 50);
      this.headingTop = reversedTop;
      this.headingLeft = reversedLeft;
      console.log("headingtop", this.headingTop);
      console.log("headingleft", this.headingLeft);
    },
    calculateTextPosition() {
      let {
        left,
        top,
        width,
        height
      } = this.$refs.text.getBoundingClientRect();
      let reversedTop =
        top >= 0 ? Math.abs(top - 220) * -1 : Math.abs(top + 20);
      let reversedLeft =
        left >= 0 ? Math.abs(left - 50) * -1 : Math.abs(left + 50);
      this.textTop = reversedTop;
      this.textLeft = reversedLeft;
      this.textWidth = window.innerWidth * 0.7;
      this.textWidthSmall = width;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
@import url("../variables.less");

.feature {
  position: relative;
  box-sizing: border-box;
  width: 31%;
  /* padding: 5px; */
  /* margin: 1%; */
  color: #fff;
  transition: transform 0.2s;
  text-align: center;
  /* -webkit-clip-path: polygon(0 0, 600px 0, 600 87%, 0 100%);
  clip-path: polygon(0 0, 600px 0, 600px 87%, 0 100%); */

  @media screen and (max-width: 800px) {
    width: 100%;
    flex-shrink: 0;
    margin-bottom: 25px;
  }
}

// .close {
//   display: block;
//   float: right;
// }

.feature.condensed:hover {
  transform: scale(1.02);
}

.inner-expanded .close {
  display: block;
}

.inner {
  position: relative;
  transform-origin: top left;
  background: rgb(65, 24, 65);
  padding: 40px 10px 20px;
  opacity: 0.5;
  height: 200px;
  -webkit-clip-path: polygon(0 8%, 100% 0%, 100% 92%, 0% 100%);
  clip-path: polygon(0 8%, 100% 0%, 100% 92%, 0% 100%);
  transition: transform 1s, opacity 1s;

  @media screen and (max-width: 800px) {
    height: 150px;
  }
}

.inner.inner-expanded {
  /* position: fixed; */
  overflow: hidden;
  z-index: 100;
  opacity: 0.95;
  clip-path: none;
  -webkit-clip-path: none;

  /* transition: none; */
}

.icon {
  position: absolute;
  height: 65px;
  top: 0;
  left: 0;
  right: 0;
  margin: -15px auto;
  z-index: 20;
  transition: all 1s;
  transform-origin: top left;
  // transition: all 1s;
}

.icon.expanded {
  z-index: 2000;
}

.text {
  position: absolute;
  top: 85px;
  transition: transform 1s;
  transform-origin: top left;

  box-sizing: border-box;
  width: 100%;

  // left: -100px;
  z-index: 10;
  text-align: left;
  padding: 15px;
  font-size: 15px;

  @media screen and (max-width: 800px) {
    font-size: 18px;
    top: 70px;
  }

  @media screen and (max-width: 580px) {
    font-size: 15px;
    top: 100px;
  }
}

.text.expanded {
  font-size: 25px;
  z-index: 1000;
}

.heading {
  position: absolute;
  top: 30px;
  transition: all 1s;
  transform-origin: top left;
  z-index: 10;
  text-align: left;
  padding: 15px;
}

.heading.expanded {
  z-index: 1000;
}

h3 {
  font-size: 35px;
  /* transform: skew(0deg, -3deg); */
  line-height: 0.8;
  font-family: @subhead;
  font-weight: bold;
  color: yellow;
  @media screen and (max-width: 800px) {
    font-size: 45px;
  }
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.05);
  }
}
</style>
