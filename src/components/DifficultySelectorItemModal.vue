<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      :id="activeModalKey + '-modal'"
      :ref="activeModalKey + '-modal'"
      tabindex="-1"
      role="dialog"
      aria-labelledby="difficulty-modal"
      aria-hidden="true"
    >
      <img
        src="../assets/pale-waiting.png"
        :class="{ 'modal-bg': true, 'modal-bg-closed': !isModalVisible }"
      />
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="difficulty-modal">
              {{ item.modal.header }}
            </h5>
            <button
              type="button"
              @mouseover="isHovering = true"
              @mouseout="isHovering = false"
              :class="{ close: true, 'close-hover': isHovering }"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body text-left" v-html="item.modal.desc"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import $ from "jquery"

export default {
  name: "DifficultySelectorItemModal",
  props: {
    item: Object,
    activeModalKey: String,
    isModalVisible: Boolean,
    isDisabled: Boolean
  },
  data: () => {
    return {
      isHovering: false
    }
  },
  mounted() {
    // capture bootstrap modal close event
    $(this.$refs[this.activeModalKey + "-modal"]).on("hidden.bs.modal", () =>
      this.$emit("closeModal")
    )
  },
  methods: {
    closeModal() {
      $(`#${this.activeModalKey}-modal`).modal("close")
    }
  }
}
</script>

<style scoped>
/* mobile/tablet/laptop/desktop */
.modal {
  user-select: none;
}
.modal-bg {
  position: absolute;
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
  font-family: "Roboto";
  padding-bottom: 1.6rem;
}
.close {
  padding: 0.2rem 0.2rem !important;
  width: 40px;
  height: 40px;
  outline: 0;
  color: #1cb9ff;
  background: #fff;
  font-size: 23px;
  font-weight: 200 !important;
  border-radius: 20px;
  opacity: 1;
}
.close-hover {
  color: #fff !important;
  background: #1cb9ff;
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

/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .close {
    margin-top: -5.04rem !important;
  }
  .modal-dialog {
    margin: 20px;
  }
  .modal-bg {
    position: relative;
    top: 48%;
    left: 0 !important;
    width: 80%;
  }
  .modal-body {
    font-size: 16px;
  }
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
  .close {
    margin: -1.6rem -4.7rem -1rem auto !important;
  }
  .modal-dialog {
    margin-top: 200px;
    width: 324px;
  }
  .modal-body {
    font-size: 13px;
  }
  .modal-bg {
    top: 22%;
  }
}
</style>
