<template>
  <div class="container">
    <div class="difficulty-selector row justify-content-center">
      <DifficultySelectorItem
        v-for="item in items"
        :item="item"
        :isFirst="item === items[0]"
        :isLast="item === items[items.length - 1]"
        v-on:updateSelectedItem="updateSelectedItem"
        v-on:onInfoClick="onInfoClick"
        v-on:setActiveModalItem="setActiveModalItem"
        :isSelected="selectedItemKey === item.key"
        v-bind:key="item.key + '-item'"
      />
    </div>
    <DifficultySelectorItemModal
      :item="activeModalItem"
      v-bind:key="activeModalItem.key"
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
      activeModalItem: {
        header: undefined,
        desc: undefined,
        modal: { header: undefined, desc: undefined }
      },
      selectedItemKey: 'ideal'
    }
  },
  methods: {
    setActiveModalItem (item) {
      if (item.isDisabled && !item.isInfoButtonHovering) {
        this.activeModalItem = {
          header: undefined,
          desc: undefined,
          modal: {
            header: 'Não disponível',
            desc: `Alguns modos podem estar desabilitados por você porque não tem cartas suficientes para estudar.
        O importante é sempre que disponível, estudar pelo modo <b> ideal </b> ok?`
          }
        }
      } else {
        this.activeModalItem = item
      }
    },
    onInfoClick (item) {
      this.isModalVisible = true
      $(`#difficulty-modal`).modal('show')
    },
    updateSelectedItem (key) {
      this.selectedItemKey = key
    },
  }
}
</script>

<style scoped>
/* mobile/tablet/laptop/desktop */
.difficulty-selector {
  user-select: none !important;
  border-radius: 10px;
  display: inline-flex;
}

/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .container {
    max-width: 900px;
  }

  .difficulty-selector {
    padding: 0 1.8rem !important;
  }
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
  .container {
    max-width: 1000px !important;
  }
  .difficulty-selector {
    padding: 0.8em 1em;
    box-shadow: 0px 3px 10px #4343431a;
    background: #ffffff;
  }
}
</style>
