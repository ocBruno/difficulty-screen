<template>
  <div
    :id="item.key"
    :class="{
      'col-sm-auto row align-self-center difficulty-selector-item': true,
      ideal: isIdeal,
      first: isFirst,
      last: isLast
    }"
  >
    <div
      @mouseover="onHover"
      @mouseout="onMouseOut"
      @click="onItemClick"
      :class="{
        translucid: !isHovering,
        opaque: isSelected
      }"
    >
      <div id="screen-more-info-button">
        <button
          @click.stop="onInfoClick"
          :class="{
            'col-sm-auto more-info-button': true,
            'more-info-button-active': !isSelected
          }"
        >
          i
        </button>
      </div>
      <DifficultyStopwatchCurtinho
        v-if="item.key === 'curtinho'"
        :isHovering="isHovering"
      />
      <DifficultyStopwatchQuaseLa
        v-if="item.key === 'quase-la'"
        :isHovering="isHovering"
      />
      <DifficultyStopwatchIdeal
        v-if="item.key === 'ideal'"
        :isHovering="isHovering"
      />
      <DifficultyStopwatchHardcore
        v-if="item.key === 'hardcore'"
        :isHovering="isHovering"
      />
      <span class="header-desc">
      <div :class="{ header: true, 'col-sm-12 header-hovering': isHovering }">
        {{ item.header }}
      </div>
      <div
        :class="{ desc: true, 'desc-hovering': isHovering }"
        v-html="item.desc"
      ></div>
      </span>
      <button
        :class="{
          'select-button mx-auto': true,
          'select-button-hovering': isHovering,
          opaque: isSelected
        }"
      >
        SELECIONAR
      </button>
    </div>
    <div id="mobile-more-info-button">
      <button
        @click.stop="onInfoClick"
        :class="{
          'more-info-button': true,
          'more-info-button-hover opaque': !isSelected
        }"
      >
        <span> i </span>
      </button>
    </div>
  </div>
</template>

<script>
import DifficultyStopwatchCurtinho from "./Stopwatches/DifficultyStopwatchCurtinho"
import DifficultyStopwatchHardcore from "./Stopwatches/DifficultyStopwatchHardcore"
import DifficultyStopwatchIdeal from "./Stopwatches/DifficultyStopwatchIdeal"
import DifficultyStopwatchQuaseLa from "./Stopwatches/DifficultyStopwatchQuaseLa"

export default {
  name: "DifficultySelectorItem",
  components: {
    DifficultyStopwatchIdeal,
    DifficultyStopwatchHardcore,
    DifficultyStopwatchCurtinho,
    DifficultyStopwatchQuaseLa
  },
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
      this.$emit("openInfoModal", this.item)
    },
    onInfoClick() {
      this.$emit("openInfoModal", this.item)
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

<style scoped>
/* mobile/tablet/laptop/desktop */
.opaque {
  opacity: 1 !important;
}
.translucid {
  opacity: 0.5;
  height: 100%;
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
.desc {
  font-family: "Fira Sans";
  font-weight: 300;
  font-size: 12px;
  color: #aaaaaa;
  margin-bottom: 10px;
  transition: transform 0.16s linear;
  transition-delay: 50ms;
  line-height: 1;
  margin-bottom: 13px;
  margin-top: 3px;
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
  font-size: 22px;
  opacity: 1;
}
.more-info-button {
  padding: 0px;
  margin-left: 1px;
  border: 2px solid #aaaaaa26;
  font-size: 11pt;
  font-family: "Roboto";
  border-radius: 24px;
  color: #1cb9ff;
  background: #fff;
  opacity: 1;
  width: 22px;
  height: 22px;
  transition: border 100ms linear;
}
#mobile-more-info-button {
  transform: scale(1.1);
  margin-left: auto;
  margin-top: auto;
  margin-bottom: auto;
}
.more-info-button:hover {
  border: 1px solid #76d4ff;
}
.more-info-button-active {
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
.stopwatch-container {
  display: inline-block;
}
button:focus {
  outline: none;
}
/* iphone 5 and other 320px */
@media (min-width: 320px) and (max-width: 340px) {
  .header-desc {
    display: inline-block;
    vertical-align: middle;
    padding-top: 0.85em;
  }
  #curtinho .translucid {
    margin-top: 0.52em;
  }  

  #quase-la .translucid {
    margin-top: 0.52em;
  }

  .stopwatch-container {
    margin-right: 0.8em !important;
  }

}
/* mobile */
@media (min-width: 340px) and (max-width: 900px) {
    .header-desc {
    padding-top: 0.5em;
  }
  #hardcore .translucid {
    margin-top: 0.52em;
  }  

  #ideal .translucid {
    margin-top: 0.52em;
  }

}
/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .header-desc {
    display: inline-block;
    vertical-align: middle;
  }
  #curtinho .translucid {
    margin-top: 0.52em;
  }  

  #quase-la .translucid {
    margin-top: 0.52em;
  }
  
  .stopwatch-container {
    margin-right: 0.8em !important;
  }
  .header {
    font-size: 14pt !important;
    font-weight: 600;
    font-family: "Fira sans";
    text-align: left !important;
    padding-top: 0;
  }
  .desc {
    margin-bottom: 6px !important;
    font-size: 11pt !important;
    font-weight: 300;
    font-family: "Fira sans";
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
  .more-info-button {
    display: inline-block;
    margin-top: auto !important;
    margin-bottom: auto !important;
    margin-left: auto !important;
    padding-bottom: 1px;
    font-weight: 700;
  }
  #screen-more-info-button {
    display: none !important;
  }

  .modal-dialog {
    position: fixed;
    top: auto;
    right: auto;
    left: auto;
    bottom: 0 !important;
  }
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
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
    font-weight: 400;
  }
  #mobile-more-info-button {
    display: none !important;
  }
}
</style>
