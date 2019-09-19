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
      statesLights: [true, false, false]
    };
  }
};
</script>
<style >
.red {
  background: red;
  opacity: 0.2;
  margin-bottom: 10px;
}
.yellow {
  background: yellow;
  opacity: 0.2;
  margin-bottom: 10px;
}
.green {
  background: green;
  opacity: 0.2;
}
</style>