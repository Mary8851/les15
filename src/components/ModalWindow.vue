<template>
  <div class="modal-window">
    <div class="modal">
      <button class="modal-close" @click="closeWindow">&#10006;</button>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalWindow",
  methods: {
    closeWindow() {
      this.$emit("closeWindow");
    },
  },
};
</script>

<style lang="scss" scoped>
.modal-window {
  position: fixed;
  top: 0;
  left: 0;
  min-height: 100%;
  width: 100%;
  background: rgba(0, 0, 0, 0.3);
  z-index: 9999;
}

.modal {
  background: linear-gradient(90deg, #68c9f0 0%, #77d5d2 100%);
  border-radius: 10px;
  padding: 20px;
  width: 400px;
  height: 100px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;

  &-close {
    color: rgb(220, 227, 228);
    font-size: 15px;
    border: none;
    background: none;
    text-align: center;
    position: absolute;
    top: 5px;
    right: 5px;
    cursor: pointer;
  }
}

// .modal-close {
//   position: absolute;
//   top: -20px;
//   right: -20px;
//   width: 40px;
//   height: 40px;
//   text-align: center;
// }
// .modal-window {
//   position: fixed;
//   z-index: 99;
//   background: rgba(0, 0, 0, 0.3);
//   top: 0;
//   left: 0;
//   right: 0;
//   bottom: 0;
//   overflow: hidden;
//   height: 100vh;
// }
// .modal {
//   position: relative;
//   top: 20%;
//   width: 50%;
//   min-height: 30vh;
//   margin: auto;
//   background: #fff;
//   padding: 20px;
//   text-align: center;
// }
</style>
