<template>
  <div class="traffic-light" :class="{ 'light--active': isActive }"></div>
</template>

<script>
export default {
  props: {
    isActive: {
      type: Boolean,
      required: true
    }
  }
};
</script>>

<style scoped>
.red {
  background: red;
}
.yellow {
  background: yellow;
}
.green {
  background: green;
}
.traffic-light {
  opacity: 0.2;
  width: 50px;
  height: 50px;
  border-radius: 50px;
  margin: 10px;
}
.light--active {
  opacity: 1;
}
</style>