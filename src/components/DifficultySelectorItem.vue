<template>
  <div class="col-sm-auto difficulty-selector-item">
    <button @click="onInfoClick" class="mx-auto more-info-button">i</button>
    <div @mouseover="onHover" @mouseout="onMouseOut" @click="onItemClick">
      <div :class="{'mt-3 stopwatch': true, 'stopwatch-bounce': isHovering}">
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
              <circle class="d" cx="13.125" cy="13.125" r="13.125" transform="translate(0)" />
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
      <div :class="{'header': true, 'header-hovering': isHovering}">{{ item.header }}</div>
      <div :class="{ 'desc': true, 'desc-hovering': isHovering }">{{ item.desc }}</div>

      <button
        :class="{
        'select-button mx-auto': true,
        'select-button-disabled': isDisabled,
        'select-button-hovering': (!isDisabled && isHovering) || isSelected
      }"
      >SELECIONAR</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "DifficultySelectorItem",
  props: {
    item: Object,
    isSelected: Boolean,
    isDisabled: Boolean
  },
  data: () => {
    return {
      isHovering: false
    };
  },
  methods: {
    onHover() {
      this.isHovering = true;
      this.$emit("setActiveModalItem", this.item);
    },
    onMouseOut() {
      this.isHovering = false;
    },
    onItemClick() {
      this.$emit("updateSelectedItem", this.item.key);
      this.$emit("updateActiveModalItem", this.item);
    },
    onInfoClick() {
      this.$emit("updateActiveModalItem", this.item);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.difficulty-selector-item {
margin: 0.48em 1.5em;
}
.difficulty-selector-item:hover {
  cursor: pointer;
  user-select: none;
}
.stopwatch {
  transition: transform 0.2s linear;
  opacity: 0.7;
}
.stopwatch-bounce {
  transform: translateY(-6px);
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

.desc {
  font-family: "Fire Sans";
  font-weight: 300;
  font-size: 12px;
  color: #aaaaaa;
  margin-bottom: 10px;
  transition: transform 0.2s linear;
  transition-delay: 50ms;
  line-height: 1;
  margin-bottom: 16px;
}
.desc-hovering,
.header-hovering {  
  transform: translateY(-1px);
}
.header {
  text-align: center;
  font-family: "Roboto";
  font-weight: 700;
  letter-spacing: 0;
  transition: transform 0.2s linear;
  transition-delay: 50ms;
  color: #000000;
  line-height: 1;
  padding: 10px 0 2px 0 !important;
  font-size: 22px;
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
  transition: border 100ms linear;
  font-weight: 700;
}
.more-info-button:hover {
  border: 1px solid #76d4ff;
}
.select-button {
  transition: transform 0.2s linear;
  width: 13em;
  height: 3.6em;
  font-family: "Fira Sans", regular;
  font-size: 10px;
  letter-spacing: 0.2px;
  color: #1cb9ff;
  background: #fff;
  border: 2px solid rgba(28, 185, 255, 0.45);
  border-radius: 24px;
  transition: color 300;
  transition-delay: 50ms;
  line-height: 3.2em;
}
.select-button-hovering {
  transform: scale(1.01);
  color: #fff;
  background-color: #4ebaff;
}
.select-button-disabled {
  opacity: 0.5 !important;
}
button:focus {
  outline: none;
}

</style>
