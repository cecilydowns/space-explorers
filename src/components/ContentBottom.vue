<template>
  <ContentBackground>
    <div class="ufo">
      <img src="../assets/ufo.svg" alt="UFO">
    </div>
    <h2>More Content</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec enim a ipsum ullamcorper sollicitudin. Vivamus aliquam rutrum semper. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per
       inceptos himenaeos. Morbi facilisis massa augue, lobortis bibendum justo vehicula sit amet. Nullam dapibus libero vel sapien rutrum, eu imperdiet nisl in
       terdum. Nunc non fringilla odio, sit amet porttitor velit..</p>
    <p>Proin blandit tortor ligula, eu dictum sapien ultricies vitae. Aenean elementum metus ut interdum mollis. Integer consequat nisi commodo ornare rhoncus. Nulla vitae elit euismod nisi tempus aliquet. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Pellentesque ipsum lectus, varius non vulputate at, ullamcorper a leo. Vestibulum et sodales tortor. Nam eget cursus nisl, id bibendum mauris. Interdum et malesuada fames ac ante ipsum primis in faucibus. Nullam sit amet metus in felis molestie mollis. Donec massa odio, varius id pellentesque sed, maximus a odio. Cras sed sapien mattis, placerat sapien et, consequat metus. Duis condimentum auctor sem in ullamcorper. Praesent congue et justo non pellentesque.</p>
  </ContentBackground>
</template>

<script>
import ContentBackground from "./ContentBackground";
export default {
  name: "ContentBottom",
  components: {
    ContentBackground
  }
};
</script>

<style scoped lang="less">
.ufo {
  float: right;
  margin-left: 10px;
  width: 300px;
  @media screen and (max-width: 675px) {
    width: 250px;
  }
  @media screen and (max-width: 575px) {
    float: none;
    width: 100%;
    text-align: center;
  }
}

.ufo img {
  @media screen and (max-width: 575px) {
    width: 90%;
  }
}
</style>
