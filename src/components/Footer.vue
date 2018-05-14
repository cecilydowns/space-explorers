<template>
  <div class="wrapper">
    <GetTheApp />
    <div id="footer">
      <div class="footer-background">
        <img src="../assets/orangeplanet.svg" alt="orange planet" class="orange-planet">
      </div>
      <div class="text">
        <p>Graphics provided by <a href="https://www.vecteezy.com">vecteezy.com</a></p>
      </div>            
    </div>
  </div>
</template>

<script>
import GetTheApp from "./GetTheApp";
export default {
  name: "Footer",
  components: {
    GetTheApp
  }
};
</script>

<style scoped lang="less">
@text-color: #c96800;

.wrapper {
  position: relative;
}

#footer {
  position: relative;
  color: #fff;
  background-size: cover;
  overflow: hidden;
  min-height: 220px;
}

.orange-planet {
  position: absolute;
  bottom: -150px;
  right: -50px;
  width: 300px;
}

.text {
  color: @text-color;
  float: left;
  margin: 160px 0 0 20px;
  text-shadow: 1px 1px 5px rgba(0, 0, 0, 1);
  position: relative;
  z-index: 100;
}

a,
a:visited {
  color: lighten(@text-color, 10%);
}

a:active,
a:hover {
  color: lighten(@text-color, 20%);
}
</style>
