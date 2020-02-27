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
              <button type="button" class="close" data-dismiss="modal" aria-label="Close">
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
.modal-title {
  text-align: left;
  font-family: "Roboto";
  font-weight: 700;
  font-size: 24px;
  color: #000000;
}
.modal-content {

  overflow: hidden
}
.modal-bg {
  height: 500px;
  background-image: url("../assets/pale-waiting.png");
  background-repeat: no-repeat;
  background-size: 362px 272px;
  background-attachment: fixed;
  background-position-x: 23rem;
}
</style>
