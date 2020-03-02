<template>
  <div class="container">
    <div class="difficulty-selector row justify-content-center">
      <DifficultySelectorItem
        v-for="item in items"
        :item="item"
        :isFirst="item === items[0]"
        :isLast="item === items[items.length - 1]"
        v-on:updateSelectedItem="updateSelectedItem"
        v-on:updateActiveModalItem="updateActiveModalItem"
        v-on:setActiveModalItem="setActiveModalItem"
        :isSelected="selectedItemKey === item.key"
        v-bind:key="item.key + '-item'"
      />
    </div>
    <DifficultySelectorItemModal
      :item="activeModalItem"
      v-on:closeModal="closeModal"
      v-bind:key="activeModalItem.key + '-modal'"
      isModalVisible
    />
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
  data: items => {
    return {
      isModalVisible: false,
      activeModalItem: {},
      selectedItemKey: 'ideal'
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
    closeModal () {
      this.isModalVisible = false
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
  user-select: none !important;
  border-radius: 10px;
  opacity: 1;
  display: inline-flex;
}

@media only screen and (min-width: 721px) and (max-width: 1960px) {
  /* Styles for laptop, desktops and other wide screens */
  .container {
    max-width: 1000px !important;
  }
  .difficulty-selector {
    padding: 0.8em 1em;
    margin-top: 1em;
    box-shadow: 0px 3px 10px #4343431a;
    background: #ffffff;
  }
}
@media (min-width: 320px) and (max-width: 720px) {
  /* Styles for mobile */
  .container {
    max-width: 900px;
  }

  .difficulty-selector {
    padding: 0 1.8rem !important;
  }
}
</style>
