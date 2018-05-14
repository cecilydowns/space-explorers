<template>
    <img src="../assets/star.svg" class="star" v-bind:style="{ 
        width: `${this.size}px`,
        top: this.top ? this.top : '',
        left: this.left ? this.left : '', 
        right: this.right ? this.right : '',
        bottom: this.bottom ? this.bottom : '',
        animationDelay: `${this.delay}s`,
        animationDuration: `${this.duration}s`
        }" />
</template>

<script>
export default {
  name: "Star",
  props: {
    size: String,
    top: String,
    bottom: String,
    right: String,
    left: String,
    duration: String,
    delay: String
  }
};
</script>

<style scoped>
.star {
  position: absolute;
  animation: twinkle infinite alternate;
  opacity: 0.8;
}

@keyframes twinkle {
  0% {
    transform: scale(1);
    opacity: 0.8;
  }
  100% {
    transform: scale(1.2) rotate(2deg);
    opacity: 1;
  }
}
</style>
