<template>
  <div id="header">     
    <h1><span>Space</span><br>Explorers</h1>
    <div class="features">
      <Feature
        title="Choose Your Starship!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="1"
      />

      <Feature
        title="Visit Alien Worlds!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="2"
      />

      <Feature
        title="A Galaxy Awaits!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="3"
      />
    </div>
  </div>
</template>

<script>
import Feature from "./Feature";

export default {
  name: "Header",
  components: {
    Feature
  }
};
</script>

<style scoped lang="less">
@import url("../variables.less");

h1 {
  font-family: @heading;
  font-size: 65px;
  color: #f47920;
  text-align: center;
  padding: 40px 10px;
  text-shadow: -1px -1px 0px#F79C1F, 1px 1px 0px rgba(0, 0, 0, 1),
    2px 2px 15px rgba(0, 0, 0, 0.7);
  transform: skew(0deg, -6deg);
  line-height: 0.8;
  z-index: 10;

  span {
    font-size: 75px;
  }

  @media screen and (max-width: 700px) {
    font-size: 55px;
    span {
      font-size: 65px;
    }
  }

  @media screen and (max-width: 400px) {
    font-size: 40px;
    span {
      font-size: 50px;
    }
  }
}
</style>
