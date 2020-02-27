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
      <div class="modal-bg">
      <div class="modal-dialog" role="document">
          <div class="modal-content">
            <div class="modal-header">
              <h5 class="modal-title" id="exampleModalLabel">{{item.header}}</h5>
              <button type="button" @mouseover="isHovering = true" @mouseout="isHovering = false" :class="{'close': true, 'close-hover' : isHovering}" data-dismiss="modal" aria-label="Close">
                <span aria-hidden="true">&times;</span>
              </button>
            </div>
            <div class="modal-body text-left">{{item.modalDesc}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DifficultySelectorItemModal",
  props: {
    item: Object
  },
  data: () => {
    return {
      isHovering: false
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
.modal-bg {
  height: 500px;
  background-image: url("../assets/pale-waiting.png");
  background-repeat: no-repeat;
  background-size: 362px 272px;
  background-attachment: fixed;
  background-position-x: 20%;
}
</style>
