<template>
    <!-- Non-expanded button -->
    <div v-if="!this.expanded" v-on:click="toggle" class="button">
        Get the App
    </div>
    <!-- Box that pops out when button is clicked -->
    <div v-else class="expanded">
      <div class="close" v-on:click="toggle">X</div>
        <div class="top">
            <span v-on:click="togglePhone" v-bind:class="this.selected === 'phone' ? 'selected' : ''">Phone</span>
            <span v-on:click="toggleEmail" v-bind:class="this.selected === 'email' ? 'selected' : ''">Email</span>
        </div>
        <div class="content">
          <!-- Wrote this as two separate forms to fix some validation message isuses I was getting, but should be able to refactor later -->
          <form @submit.prevent="handleSubmit" v-bind:class="this.selected === 'phone' ? 'form' : 'form hidden'">
            <input ref="phoneinput" v-validate="'required|numeric'" name="phone" type="text" v-model="number" placeholder="We'll text you a link" />                 
            <button>Go</button>
            <div class="errors">{{ errors.first('phone')}}</div>
          </form>

          <form @submit.prevent="handleSubmit" v-bind:class="this.selected === 'email' ? 'form' : 'form hidden'">
            <input ref="emailinput" v-validate="'required|email'" name="email" type="text" v-model="email" placeholder="We'll email you a link" />
            <button>Go</button>
            <div class="errors">{{ errors.first('email')}}</div>
          </form>          

          <div class="store-icons">
            <img src="../assets/ios.svg">
            <img src="../assets/android.svg">
          </div>
        </div>
    </div>
</template>

<script>
export default {
  name: "GetTheApp",
  data() {
    return {
      expanded: false,
      selected: "email",
      number: "",
      email: ""
    };
  },
  methods: {
    toggle(event) {
      this.expanded === true ? (this.expanded = false) : (this.expanded = true);
    },
    togglePhone(event) {
      this.selected = "phone";
      this.$refs.phoneinput.focus();
    },
    toggleEmail(event) {
      this.selected = "email";
      this.$refs.emailinput.focus();
    },
    handleSubmit(event) {
      // Just console.logging the phone or email for now - can hook up to a backend eventually!
      if (this.selected === "email") {
        console.log(this.email);
      } else {
        console.log(this.number);
      }
    }
  }
};
</script>

<style scoped lang="less">
@import url("../variables.less");

/* Non-expanded "get the app" button */
.button {
  font-family: "Luckiest Guy";
  font-size: 25px;
  position: absolute;
  top: -50px;
  right: 0;
  left: 0;
  margin: 10px auto;
  width: 150px;
  padding: 15px;
  text-align: center;
  background: #febf04;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.2);
  z-index: 10;
  background-image: linear-gradient(to bottom, #ffd65e, #febf04);
  transition: transform 0.1s;
  cursor: default;
}

.button:hover {
  transform: scale(1.03);
}

/* Expanded box */
.expanded {
  position: absolute;
  top: -70px;
  right: 0;
  left: 0;
  margin: 10px auto;
  width: 300px;
  text-align: center;
  box-shadow: 1px 1px 15px rgba(0, 0, 0, 0.4);
  background-image: linear-gradient(to bottom, #ffd65e, #febf04);
  animation: enter 0.2s 1;
  z-index: 1000;
  padding: 15px;
}

.close {
  float: right;
  font-family: "Luckiest Guy";
  cursor: default;
}

/* Phone / Email options at top of box */
.top span {
  display: inline-block;
  opacity: 0.5;
  transition: all 0.1s;
  font-family: "Unica One";
  font-size: 20px;
  padding: 0 15px 10px;
  cursor: default;
}

.top span.selected {
  font-weight: bold;
  opacity: 1;
}

/* Form positioning and visibility */
.form {
  position: absolute;
  left: 0;
  right: 0;
  margin: 0 auto;
  top: 50px;
  opacity: 1;
}

.form.hidden {
  opacity: 0;
  display: none;
}

/* Form input and button */
input,
button {
  box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.1);
  display: inline-block;
  vertical-align: top;
  border: none;
  outline: none;
}

input {
  padding: 10px;
  font-size: 15px;
  width: 200px;
  font-family: "Avenir";
}

button {
  font-family: "Unica One";
  background: orange;
  font-size: 30px;
  background-image: linear-gradient(to bottom, #f18900, darken(#f18900, 10%));
  color: #fff;
  transition: transform 0.1s;
}

button:hover {
  transform: scale(1.05);
}

/* Input error message styling */
.errors {
  font-family: "Avenir";
  font-size: 12px;
  margin-top: 3px;
}

/* iOS / Google app store icons */
.store-icons {
  margin-top: 65px;
}

.store-icons img {
  width: 120px;
}

/* Keyframes */
@keyframes enter {
  0% {
    transform: scale(0.4);
    opacity: 0.4;
  }
  85% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
</style>