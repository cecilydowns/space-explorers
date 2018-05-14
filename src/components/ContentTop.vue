<template>
  <div class="wrapper">
    <img src="../assets/phone.png" class="phone" />
    <ContentBackground>
      <div class="right">
        <h2>Welcome!</h2>

        <p>This is a promotional website for a made-up game that I built to try out the <a href="https://vuejs.org/">Vue</a>
        JavaScript framework. I also used the opportunity to design a more playful, fun style of site and to try using
        performant CSS animation using the <a href="https://medium.com/outsystems-experts/flip-your-60-fps-animations-flip-em-good-372281598865">FLIP techinque</a>.
        The design is fully responsive, with the exception of the modal display issues noted below.
        </p>

        <h2>To do still</h2>
        <ul>
          <li>Clicking on a feature (one of the boxes in the three-column grid)
            will expand the item into a full-screen modal, but more work needs to be done
            on the positioning of elements in this view, making sure it works at every screen size,
            and ensuring the elements will reposition after window resize.</li>
          <li>Clicking on the "Get the App" button at the bottom of the page will open a form with text/email input options.
            Submitting the form will log the chosen input to the console. I still need to connect it to
            a backend and provide a visual indication of the form being submitted.
          </li>
        </ul>
      </div>
    </ContentBackground>
  </div>
</template>

<script>
import ContentBackground from "./ContentBackground";
export default {
  name: "ContentTop",
  components: {
    ContentBackground
  }
};
</script>

<style scoped lang="less">
@import url("../variables.less");

.wrapper {
  position: relative;
}

.right {
  margin-left: 250px;
  @media screen and (max-width: 700px) {
    margin-left: 215px;
  }
  @media screen and (max-width: 575px) {
    margin-left: 190px;
  }

  @media screen and (max-width: 525px) {
    margin-left: 0;
    margin-top: 490px;
  }

  @media screen and (max-width: 350px) {
    margin-top: 390px;
  }
}

.phone {
  width: 235px;
  position: absolute;
  box-sizing: border-box;
  top: -15px;
  left: 30px;
  z-index: 10;
  @media screen and (max-width: 700px) {
    width: 200px;
  }
  @media screen and (max-width: 575px) {
    width: 175px;
  }
  @media screen and (max-width: 525px) {
    left: 0;
    right: 0;
    width: 270px;
    margin: 0 auto;
  }

  @media screen and (max-width: 350px) {
    width: 220px;
  }
}
</style>
