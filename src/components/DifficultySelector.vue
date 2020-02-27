<template>
  <div class="container">
    <div class="row mx-auto mt-3 py-3 difficulty-selector">
      <DifficultySelectorItem v-on:updateActiveModalItem="updateActiveModalItem" v-on:setActiveModalItem="setActiveModalItem" :item="{...item}" v-for="item in items" v-bind:key="item.key + '-item'"/>
      <DifficultySelectorItemModal :item="activeModalItem" v-bind:key="activeModalItem.key + '-modal'"/>
      
    
    </div>
  </div>
</template>

<script>
import DifficultySelectorItem from './DifficultySelectorItem'
import DifficultySelectorItemModal from "./DifficultySelectorItemModal";
import $ from 'jquery'

export default {
  name: 'DifficultySelector',
  components: {DifficultySelectorItem, DifficultySelectorItemModal},
  props: {
    items: Array,
  },
  data: () => {
    return {
      isSelected: false,
      isModalVisible: false,
      activeModalItem: {}

    }
  },
  methods: {
    updateActiveModalItem() { 
      this.isModalVisible = true
      this.showModal(this.activeModalItem.key)
    },
    setActiveModalItem(item) { 
      this.activeModalItem = item
    },
    showModal(key) {
      $(`#${key}-modal`).modal('show')
    } 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.difficulty-selector {
  width: 866px;
  height: 240px;
  background: #FFFFFF;
  box-shadow: 0px 3px 10px #4343431A;
  border-radius: 10px;
  opacity: 1;
}
</style>
