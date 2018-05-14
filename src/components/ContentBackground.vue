<template>
        <div class="content">
           <slot></slot>
        </div>
</template>

<script>
export default {
  name: "ContentBackground"
};
</script>

<style scoped lang="less">
@import url("../variables.less");

.content {
  display: block;
  background: rgba(255, 255, 255, 0.95);
  font-size: 20px;
  -webkit-clip-path: polygon(0 5%, 100% 0%, 100% 95%, 0% 100%);
  clip-path: polygon(0 5%, 100% 0%, 100% 95%, 0% 100%);
  padding: 50px 40px;
  @media screen and (max-width: 600px) {
    font-size: 18px;
  }
  @media screen and (max-width: 400px) {
    padding: 50px 25px;
  }
}

h2 {
  font-size: 40px;
  color: @purple;
  font-family: @subhead;
  font-weight: bold;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
  background: url("../assets/rock.svg");
  background-size: 25px;
  background-repeat: no-repeat;
  background-position: left 0 top 0;
  padding-left: 40px;
  margin-bottom: 15px;
}
</style>
