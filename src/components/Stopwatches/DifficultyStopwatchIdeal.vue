<template>
  <div class="stopwatch-container">
    <div
      :class="{
        'stopwatch stopwatch-screen': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/ideal-screen.png" alt="Ideal" />
    </div>
    <div
      :class="{
        'stopwatch stopwatch-mobile': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/ideal-mobile.png" alt="Ideal" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DifficultyStopwatchIdeal',
  props: {
    isHovering: Boolean
  },
  data: () => {return {}}
}
</script>

<style scoped>
/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .stopwatch-container {
    transform: scale(1.2), translateY(2em);
  }
  
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {

}
</style>
