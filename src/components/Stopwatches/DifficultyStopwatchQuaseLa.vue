<template>
  <div class="stopwatch-container">
    <div
      :class="{
        'stopwatch stopwatch-screen': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/quase-la-screen.png" alt="Ideal" />
    </div>
    <div
      :class="{
        'stopwatch stopwatch-mobile': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/quase-la-mobile.png" alt="Ideal" />
    </div>
  </div>
</template>

<script>
export default {
  name: "DifficultyStopwatchQuaseLa",
  props: {
    isHovering: Boolean
  },
  data: () => {
    return {}
  }
}
</script>

<style scoped>
/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
  .a {
    fill: #f6d476;
  }
  .b {
    fill: #1cb9ff;
  }
  .c {
    clip-path: url(#a);
  }
  .d {
    fill: #fff;
  }
  .e {
    fill: #ffda72;
  }
}
</style>
