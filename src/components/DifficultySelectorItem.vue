<template>
  <div
    class="col-sm difficulty-selector-item"
    @mouseover="isHovering = true"
    @mouseout="isHovering = false"
  >
    <button class="mx-auto more-info-button">i</button>
    <div class="header">{{ item.header }}</div>
    <div class="desc">{{ item.desc }}</div>

    <button
      :class="{ 'select-button mx-auto': true, 'select-button-hovering': isHovering }"
    >
      Selecionar
    </button>
  </div>
</template>

<script>
export default {
  name: 'DifficultySelectorItem',
  props: {
    item: Object
  },
  data: () => {
    return {
      isHovering: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Fira+Sans:300,400&display=swap');
@import url('https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap');
.difficulty-selector-item {
  width: 140px;
  height: 188px;
}
.desc {
  font-family: 'Fire Sans';
  font-weight: 300;
  font-size: 12px;
  color: #AAAAAA;
}
.header {
  text-align: center;
  font-family: 'Roboto';
  font-weight: 700;
  letter-spacing: 0;
  color: #000000;
  font-size: 24px;
  opacity: 1;
}
.more-info-button {
  width: 20px;
  height: 20px;
  border: 2px solid #aaaaaa26;
  border-radius: 24px;
  color: #1cb9ff;
  background: #fff;
  opacity: 1;
}
.select-button {
  width: 133px;
  height: 36px;
  font-family: 'Fira Sans', regular;
  font-size: 10px;
  letter-spacing: 0.2px;
  color: #1cb9ff;
  border: 2px solid #1cb9ff;
  border-radius: 24px;
  opacity: 0.45;
}
.select-button-hovering {
  color: #fff;
  background-color: #1cb9ff;
}
</style>
