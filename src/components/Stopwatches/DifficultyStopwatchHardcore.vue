<template>
  <div class="stopwatch-container">
     <div
      :class="{
        'stopwatch stopwatch-screen': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/hardcore-screen.png" alt="Ideal" />
    </div>
    <div
      :class="{
        'stopwatch stopwatch-mobile': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="../../assets/png/hardcore-mobile.png" alt="Ideal" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DifficultyStopwatchHardcore',
  props: {
    isHovering: Boolean
  },
  data: () => {return {}}
}
</script>

<style scoped>
@media (min-width: 320px) and (max-width: 720px) {
  /* mobile */
}
@media (min-width: 721px) and (max-width: 1960px) {

  /* tablet/laptop/desktop */

}
</style>
