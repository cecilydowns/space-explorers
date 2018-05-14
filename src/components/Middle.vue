<template>
  <div id="middle">   
    <h3>More Features</h3>
    <div class="features">
      <Feature
        title="Even More Spaceships!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="4"
      />
      <Feature
        title="Blaster Rays!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="5"
      />
      <Feature
        title="Renewable Energy!"
        content="Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis elementum leo et ipsum accumsan, ac viverra dui lobortis."
        icon="6"
      />
    </div>
  </div>
</template>

<script>
import Feature from "./Feature";

export default {
  name: "Middle",
  components: {
    Feature
  }
};
</script>

<style scoped>
h3 {
  font-size: 40px;
  color: #f47920;
  text-align: center;
  padding: 25px 10px;
  text-shadow: -1px -1px 0px#F79C1F, 1px 1px 0px rgba(0, 0, 0, 1),
    2px 2px 15px rgba(0, 0, 0, 0.7);
  transform: skew(0deg, -3deg);
  line-height: 45px;
  z-index: 10;
}
</style>
