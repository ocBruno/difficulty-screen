<template>
  <div>
    <!-- Modal -->
    <div
      class="modal fade"
      id="difficulty-modal"
      ref="difficulty-modal"
      tabindex="-1"
      role="dialog"
      aria-labelledby="difficulty-modal"
      aria-hidden="true"
    >
      <img
        src="../assets/png/pale-waiting.png"
        class="modal-bg"
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
import $ from 'jquery'

export default {
  name: 'DifficultySelectorItemModal',
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
  mounted () {
    // capture bootstrap modal close event

  },
  methods: {
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
  left: 18.4%;
  opacity: 1;
  transition: opacity 150ms ease-in-out;
  pointer-events: none;
}
.modal-content {
  padding-left: 0.8em !important;
}
.modal-header {
  border-bottom: 0px;
  padding-bottom: 0.2rem;
  padding-top: 0.8rem;
}
.modal-body {
  font-family: 'Roboto';
  padding-bottom: 1.2rem;
  padding-top: 0.2rem;
}
.close {
  display: flex;
  opacity: 1;
  padding: 0 !important;
  width: 40px;
  height: 40px;
  outline: 0;
  border-radius: 20px;
  color: #1cb9ff;
  background: #fff;
  font-family: 'Roboto';
  font-size: 1.48em;
  transition: color 0.12s linear;

  font-weight: 300 !important;
}
.close > span {
  display: flex;
  margin: auto auto 0.12em auto;
}
.close-hover {
  color: #fff !important;
  background: #1cb9ff;
  font-weight: 100 !important;
}
.close-hover > span {
  margin: auto auto 0.28em auto;
}
.modal-title {
  text-align: left;
  font-family: 'Roboto';
  font-weight: 700;
  font-size: 1.44em;
  color: #000000;
}
.modal-content {
  border-radius: 20px;
  padding: 10px;
}

/* mobile */
@media (min-width: 320px) and (max-width: 720px) {
  .modal-open .modal { 
  background: #000000cf;
}
  .modal-header .close {
    transform: scale(1.24);
  }
  .close {
    margin-top: -5.04rem !important;
  }
  .modal-dialog {
    margin: 20px;
  }
  .modal-bg {
    position: relative;
    top: 25%;
    left: 0 !important;
    width: 80%;
  }
  .modal-title {
   font-size: 1.8em; 
  }
  .modal-body {
    line-height: 1.36;
    font-size: 16px;
  }
}

/* tablet/laptop/desktop */
@media (min-width: 721px) and (max-width: 1960px) {
  .close {
    margin: -1.6rem -4.7rem -1rem auto !important;
  }
    .modal-open .modal { 
  background: #0000006b;
}
  .modal-dialog {
    margin-top: 200px;
    width: 20.8rem;
  }
  .modal-body {
    font-size: 0.8em;
  }
  .modal-bg {
    top: 24%;
    width: 28.8%;
  }
}
</style>
