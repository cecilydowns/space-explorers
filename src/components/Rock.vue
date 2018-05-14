<template>
    <img v-bind:src="require(`../assets/rock${this.type}.svg`)" class="rock" v-bind:style="{ 
        width: `${this.size}px`,
        top: this.top ? this.top : '',
        left: this.left ? this.left : '', 
        right: this.right ? this.right : '',
        bottom: this.bottom ? this.bottom : ''
        }" />
</template>

<script>
export default {
  name: "Rock",
  props: {
    size: String,
    top: String,
    bottom: String,
    right: String,
    left: String,
    type: String
  }
};
</script>

<style scoped>
.rock {
  position: absolute;
}
</style>