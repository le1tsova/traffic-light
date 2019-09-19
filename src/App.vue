<template>
  <div id="app">
    <v-light class="red" v-bind:is-active="statesLights[0]"></v-light>
    <v-light class="yellow" v-bind:is-active="statesLights[1]"></v-light>
    <v-light class="green" v-bind:is-active="statesLights[2]"></v-light>
  </div>
</template>

<script>
import VLight from "./components/Signal.vue";

export default {
  name: "app",
  components: {
    VLight
  },
  data() {
    return {
      statesLights: [false, false, false]
    };
  },
  methods: {
    setLight(objLights) {
      let pathname;

      if (objLights === ORDER.red) {
        this.statesLights = [true, false, false];
        pathname = "/1";
      } else if (objLights === ORDER.green) {
        this.statesLights = [false, false, true];
        pathname = "/3";
      } else {
        this.statesLights = [false, true, false];
        pathname = "/2";
      }

      window.history.pushState(null, "", pathname);

      setTimeout(
        this.setLight.bind(this),
        objLights.period * 1000,
        objLights.next
      );
    }
  },
  beforeMount() {
    let startIndex = parseInt(window.location.pathname.slice(-1), 10);
    const identifiers = {
      1: ORDER.red,
      2: ORDER.yellow,
      3: ORDER.green
    };

    if (!startIndex) {
      startIndex = Math.floor(
        1 + Math.random() * Object.keys(identifiers).length
      );
    }

    this.setLight(identifiers[startIndex]);
  }
};

const ORDER = {
  red: {
    period: 10,
    get next() {
      return ORDER.yellow2;
    }
  },
  yellow: {
    period: 3,
    get next() {
      return ORDER.red;
    }
  },
  yellow2: {
    period: 3,
    get next() {
      return ORDER.green;
    }
  },
  green: {
    period: 15,
    get next() {
      return ORDER.yellow;
    }
  }
};
</script>
<style >
</style>