<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      :id="item.key + '-modal'"
      :ref="item.key + '-modal'"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
      
    >
      <img src="../assets/pale-waiting.png" :class="{'modal-bg': true, 'modal-bg-closed': !this.isModalVisible}"/>
    
      <div class="modal-dialog" role="document">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel">{{item.modalHeader}}</h5>
              <button type="button" @mouseover="isHovering = true" @mouseout="isHovering = false" :class="{'close': true, 'close-hover' : isHovering}" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
            <div class="modal-body text-left" v-html="item.modalDesc"></div>
          </div>
        </div>
      </div>

  </div>
</template>

<script>
import $ from 'jquery'

export default {
  name: "DifficultySelectorItemModal",
  props: {
    item: Object,
    isModalVisible: Boolean
  },
  data: () => {
    return {
      isHovering: false
    };
  },
  mounted() {
    // capture bootstrap modal close event
    $(this.$refs[this.item.key + '-modal']).on("hidden.bs.modal", ()=>this.$emit('closeModal')
)
  },
  methods: {
    closeModal(key) {
      $(`#${key}-modal`).modal('close')
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.modal {
  user-select: none;
}
.modal-bg {
  position: absolute;
  top: 22%;
  left: 22%;
  opacity: 1;
  transition: opacity 150ms ease-in-out;
  pointer-events: none;

}
.modal-bg-closed {
    opacity: 0;
} 
.modal-header {
  border-bottom: 0px;
  padding-bottom: 0.2rem;
}
.modal-body {
  padding-top: 0.2rem;
  font-family: 'Roboto';
  font-size: 12px;
  padding-bottom: 3rem;

}
.close {
  margin: -1rem -5rem -1rem auto !important;
  padding: 0.4rem 0.4rem !important;
  width: 40px;
  color: #1CB9FF; 
  background: #fff;
  font-size: 28px;
  font-weight: 200 !important;
  border-radius: 19px;
  opacity: 1;
}

.close-hover {
  color: #fff !important; 
  background: #1CB9FF;

}
.modal-title {
  text-align: left;
  font-family: "Roboto";
  font-weight: 700;
  font-size: 24px;
  color: #000000;
}
.modal-content {
  border-radius: 20px;
  padding: 10px;
}
/* laptop and most screens */
@media only screen and (min-width: 1200px) {
  .modal-dialog {
  margin-top: 200px;
  width: 324px;
}
}
</style>
