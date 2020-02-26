<template>
  <div class="container">
    <div class="row difficulty-selector">
      <DifficultySelectorItem :item="item" v-for="item in items" v-bind:key="item.header" />
    </div>
  </div>
</template>

<script>
import DifficultySelectorItem from './DifficultySelectorItem'
export default {
  name: 'DifficultySelector',
  components: {DifficultySelectorItem},
  props: {
    items: Array
  },
  data: () => {
    return {
      isSelected: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.dificulty-selector {
  top: 554px;
  left: 250px;
  width: 866px;
  height: 240px;
  background: #FFFFFF 0% 0% no-repeat padding-box;
  box-shadow: 0px 3px 10px #4343431A;
  border-radius: 10px;
  opacity: 1;
}
</style>
