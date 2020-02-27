<template>
  <div class="container">
    <div class="row mx-auto mt-3 py-3 difficulty-selector">
      <DifficultySelectorItem
        v-for="item in items"
        :item="item"
        v-on:updateSelectedItem="updateSelectedItem"
        v-on:updateActiveModalItem="updateActiveModalItem"
        v-on:setActiveModalItem="setActiveModalItem"
        :isSelected="selectedItemKey === item.key "
        v-bind:key="item.key + '-item'"
      />
      <DifficultySelectorItemModal
        :item="activeModalItem"
        v-bind:key="activeModalItem.key + '-modal'"
      />
    </div>
  </div>
</template>

<script>
import DifficultySelectorItem from './DifficultySelectorItem'
import DifficultySelectorItemModal from './DifficultySelectorItemModal'
import $ from 'jquery'

export default {
  name: 'DifficultySelector',
  components: { DifficultySelectorItem, DifficultySelectorItemModal },
  props: {
    items: Array
  },
  data: () => {
    return {
      isModalVisible: false,
      activeModalItem: {},
      selectedItemKey: undefined
    }
  },
  methods: {
    updateActiveModalItem () {
      this.isModalVisible = true
      this.showModal(this.activeModalItem.key)
    },
    updateSelectedItem (key) {
      this.selectedItemKey = key
    },
    setActiveModalItem (item) {
      this.activeModalItem = item
    },
    showModal (key) {
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
  background: #ffffff;
  box-shadow: 0px 3px 10px #4343431a;
  border-radius: 10px;
  opacity: 1;
}
</style>
