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
.traffic-light {
  width: 50px;
  height: 50px;
  border-radius: 50px;
}
.light--active {
  opacity: 1;
}
</style>