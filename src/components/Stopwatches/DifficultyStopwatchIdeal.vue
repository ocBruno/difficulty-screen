<template>
  <div class="d-inline-flex stopwatch-container">
    <div
      :class="{
        'stopwatch stopwatch-screen': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        width="52"
        height="52"
        viewBox="0 0 52 52"
      >
        <defs style>
          <clipPath id="a">
            <circle class="a" cx="13.125" cy="13.125" r="13.125" />
          </clipPath>
        </defs>
        <circle class="b" cx="26" cy="26" r="26" />
        <g transform="translate(11 7)">
          <g class="c" transform="translate(1.667 7.383)">
            <circle
              class="d"
              cx="13.125"
              cy="13.125"
              r="13.125"
              transform="translate(0)"
            />
            <path
              class="e"
              d="M26,15.484V31.972H42.184V17.167l-2.222-4.542Z"
              transform="translate(-12.667 -17.41)"
            />
          </g>
          <path
            class="d"
            d="M24.5,1.5h-10V4.833h10Zm6.717,10.65,2.367-2.367a18.414,18.414,0,0,0-2.35-2.35L28.867,9.8a15,15,0,1,0,2.35,2.35ZM19.5,33.167A11.667,11.667,0,1,1,31.167,21.5,11.658,11.658,0,0,1,19.5,33.167Z"
            transform="translate(-4.5 -1.5)"
          />
        </g>
      </svg>
    </div>
    <div
      id="stopwatch-mobile"
      :class="{
        'stopwatch stopwatch-mobile': true,
        'stopwatch-bounce': isHovering
      }"
    >
      <img src="./png/ideal.png" alt="Ideal" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'DifficultyStopwatchIdeal',
  props: {
    isHovering: Boolean
  },
  data: () => {
    return {
      windowWidth: 0
    }
  }
}
</script>

<style scoped>
/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .stopwatch-container {
    margin-right: 2em !important;
    transform: scale(1.2), translateY(2em);
  }
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
