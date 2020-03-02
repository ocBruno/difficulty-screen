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
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        width="24"
        height="28"
        viewBox="0 0 24 28"
      >
        <defs>
          <clipPath id="a">
            <circle class="a" cx="10.5" cy="10.5" r="10.5" />
          </clipPath>
        </defs>
        <g class="b" transform="translate(1.333 5.906)">
          <circle
            class="c"
            cx="10.5"
            cy="10.5"
            r="10.5"
            transform="translate(0)"
          />
          <path
            class="d"
            d="M17.19,13.633l-3.4,12.56,7.092,11.969,18.063-3.868V16.258L37.17,12.625Z"
            transform="translate(-15.333 -16.453)"
          />
        </g>
        <path
          class="e"
          d="M20.5,1.5h-8V4.167h8Zm5.373,8.52,1.893-1.893a14.731,14.731,0,0,0-1.88-1.88L23.993,8.14a12,12,0,1,0,1.88,1.88ZM16.5,26.833A9.333,9.333,0,1,1,25.833,17.5,9.327,9.327,0,0,1,16.5,26.833Z"
          transform="translate(-4.5 -1.5)"
        />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "DifficultyStopwatchIdeal",
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@media (min-width: 320px) and (max-width: 480px) {
  /* mobile */
  .stopwatch-container {
    margin-right: 2em !important;
    transform: scale(1.2), translateY(2em);
  }

  .a {
    fill: #00aee0;
  }
  .b {
    clip-path: url(#a);
  }
  .c {
    fill: #fff;
  }
  .d {
    fill: #1cb9ff;
  }
  .e {
    fill: #0027c5;
  }
}
@media (min-width: 1000px) and (max-width: 1960px) {
  /* laptop desktop screens */

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

.stopwatch {
  transition: transform 0.16s linear;
  opacity: 0.7;
}
.stopwatch-bounce {
  transform: translateY(-6px);
  opacity: 1;
}
</style>
