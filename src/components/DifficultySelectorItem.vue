<template>
  <div
    class="col-sm difficulty-selector-item"
    @mouseover="onHover"
    @mouseout="isHovering = false"
    @click="onClick"
  >
    <button class="mx-auto more-info-button">
      i
    </button>
    <div :class="{'mt-3 stopwatch': true, 'stopwatch-bounce': isHovering}">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        width="52"
        height="52"
        viewBox="0 0 52 52"
      >
        <defs style="">
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
    <div class="header">{{ item.header }}</div>
    <div :class="{ 'desc': true, 'desc-hovering': isHovering }">
      {{ item.desc }}
    </div>

    <button
      :class="{
        'select-button mx-auto': true,
        'select-button-disabled': isDisabled,
        'select-button-hovering': (!isDisabled && isHovering) || isSelected
      }"
    >
      SELECIONAR
    </button>
  </div>
</template>

<script>
export default {
  name: 'DifficultySelectorItem',
  props: {
    item: Object,
    isSelected: Boolean,
    isDisabled: Boolean
  },
  data: () => {
    return {
      isHovering: false
    }
  },
  methods: {
    onHover () {
      this.isHovering = true
      this.$emit('setActiveModalItem', this.item)
    },
    onClick () {
      this.$emit('updateSelectedItem', this.item.key)
      this.$emit('updateActiveModalItem', this.item)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.difficulty-selector-item:hover {
  cursor: pointer;
}
.stopwatch{
  transition: transform 0.2s ease-in;
  opacity: 0.7;
}
.stopwatch-bounce{
  transform: translateY(-8px);
  opacity: 1;
}
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
.difficulty-selector-item {
  width: 140px;
  height: 188px;
}
.desc {
  font-family: 'Fire Sans';
  font-weight: 300;
  font-size: 12px;
  color: #aaaaaa;
  margin-bottom: 10px;
}
.header {
  text-align: center;
  font-family: 'Roboto';
  font-weight: 700;
  letter-spacing: 0;
  color: #000000;
  line-height: 1;
  padding: 10px 0 2px 0 !important;
  font-size: 24px;
  opacity: 1;
}
.more-info-button {
  border: 2px solid #aaaaaa26;
  border-radius: 24px;
  color: #1cb9ff;
  background: #fff;
  opacity: 1;
  font-size: 11px;
  width: 20px;
  font-weight: 700;
}
.select-button {
  width: 133px;
  height: 36px;
  font-family: 'Fira Sans', regular;
  font-size: 10px;
  letter-spacing: 0.2px;
  color: #1cb9ff;
  background: #fff;
  border: 2px solid #1cb9ff;
  border-radius: 24px;
  transition: color 300;
}
button:focus {
  outline: none;
}
.select-button-hovering {
  color: #fff;
  background-color: #4ebaff;
}
.desc-hovering {
  font-weight: 700;
}
</style>
