<template>
  <div
    :class="{
      'col-sm-auto row align-self-center difficulty-selector-item': true,
      ideal: isIdeal,
      first: isFirst,
      last: isLast
    }"
  >
    <div @mouseover="onHover" @mouseout="onMouseOut" @click="onItemClick">
      <button
        @click.stop="onInfoClick"
        id="screen-more-info-button"
        :class="{
          'col-sm-auto more-info-button': true,
          opaque: !isSelected
        }"
      >
        i
      </button>
      <div :class="{ opaque: isSelected }">
        <DifficultyStopwatchHardcore :isHovering="isHovering" />
        <span class="header-desc">
          <div :class="{ header: true, 'header-hovering': isHovering }">
            {{ item.header }}
          </div>
          <div :class="{ desc: true, 'desc-hovering': isHovering }">
            {{ item.desc }}
          </div>
          <button
            @click.stop="onInfoClick"
            id="mobile-more-info-button"
            :class="{
              'more-info-button': true,
              'more-info-button-hover opaque': !isSelected
            }"
          >
            i
          </button>
        </span>
        <button
          :class="{
            'select-button mx-auto': true,
            'select-button-hovering': isHovering,
            translucid: !isHovering,
            opaque: isSelected
          }"
        >
          SELECIONAR
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import DifficultyStopwatchHardcore from "./Stopwatches/DifficultyStopwatchHardcore"
export default {
  name: "DifficultySelectorItem",
  components: { DifficultyStopwatchHardcore },
  props: {
    item: Object,
    isDisabled: Boolean,
    isSelected: Boolean,
    isFirst: Boolean,
    isLast: Boolean
  },
  data: () => {
    return {
      isHovering: false
    }
  },
  methods: {
    onHover() {
      this.isHovering = true
      this.$emit("setActiveModalItem", this.item)
    },
    onMouseOut() {
      this.isHovering = false
    },
    onItemClick() {
      this.$emit("updateSelectedItem", this.item.key)
      this.$emit("updateActiveModalItem", this.item)
    },
    onInfoClick() {
      this.$emit("updateActiveModalItem", this.item)
    }
  },
  mounted() {},
  computed: {
    isIdeal() {
      return this.item.key === "ideal"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@media (min-width: 320px) and (max-width: 720px) {
  /* mobile */
  .more-info-button {
    display: inline-block;
    margin-left: 8em !important;
  }
  #screen-more-info-button {
    display: none !important;
  }
  .ideal {
    border: #ffbb00 2pt solid;
  }

  .difficulty-selector-item {
    min-width: 6rem;
    background: #fff;
    border-radius: 20px;
    height: 4.8rem;
    margin: 0.48em 0em !important;
  }
  .select-button {
    display: none !important;
    visibility: hidden !important;
  }
  .header {
    font-size: 14pt !important;
    font-weight: 600;
    font-family: "Fira sans";
    text-align: left !important;
  }
  .header-desc {
    display: inline-block !important;
  }
  .stopwatch {
    display: inline-block !important;
    margin-right: 1rem;
  }
  .desc {
    margin-bottom: 6px !important;
    font-size: 12pt !important;
    font-weight: 300;
    font-family: "Fira sans";
  }
}
@media (min-width: 1000px) and (max-width: 1960px) {
  /* laptop desktop screens */
  .first {
    margin-left: 0 !important;
  }
  .last {
    margin-right: 0 !important;
  }
  .more-info-button {
    display: inline-block !important;
    width: 20px !important;
    margin-bottom: 1.2em;
  }
  #mobile-more-info-button {
    display: none !important;
  }
}
.opaque {
  opacity: 1 !important;
}
.translucid {
  opacity: 0.5;
}

.header-desc {
  display: block;
}
.difficulty-selector-item {
  margin: 0.68em 1.6em;
}
.difficulty-selector-item:hover {
  cursor: pointer;
  user-select: none;
}
.stopwatch {
  transition: transform 0.16s linear;
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
  transition: transform 0.16s linear;
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
  transition: transform 0.16s linear;
  transition-delay: 50ms;
  color: #000000;
  line-height: 1;
  padding: 10px 0 2px 0 !important;
  font-size: 22px;
  opacity: 1;
}
.more-info-button {
  padding: 0px;
  margin-left: 1px;
  border: 2px solid #aaaaaa26;
  border-radius: 24px;
  color: #1cb9ff;
  background: #fff;
  opacity: 1;
  font-size: 11px;
  width: 20px;
  transition: border 100ms linear;
}
.more-info-button:hover {
  border: 1px solid #76d4ff;
}
.select-button {
  transition: transform 0.16s linear;
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

button:focus {
  outline: none;
}
</style>
