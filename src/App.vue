<template>
  <div id="app">
      <Background />
      <Header />
      <ContentTop />
      <Middle />
      <ContentBottom />
      <Footer/>
    </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import Background from "./components/Background";
import ContentTop from "./components/ContentTop";
import ContentBottom from "./components/ContentBottom";
import Middle from "./components/Middle";

export default {
  name: "App",
  components: {
    Header,
    Footer,
    Background,
    ContentTop,
    ContentBottom,
    Middle
  }
};
</script>


<style>
@import url("https://fonts.googleapis.com/css?family=Luckiest+Guy|Unica+One");
</style>

<style lang="less">
@import url("./variables.less");

body {
  margin: 0;
  padding: 0;
}

body.modal {
  overflow: hidden;
  height: 100vh;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}

h1,
h2,
h3,
h4,
h5 {
  font-family: "Luckiest Guy";
  letter-spacing: 1px;
  font-weight: normal;
  margin: 0;
}

a,
a:visited {
  color: @purple;
}

a:hover {
  color: lighten(@purple, 10%);
}

a:active {
  color: lighten(@purple, 0%);
}

.features {
  padding: 40px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  @media screen and (max-width: 400px) {
    padding: 25px;
  }
}
</style>
