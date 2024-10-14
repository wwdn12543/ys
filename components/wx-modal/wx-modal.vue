<template>
  <div class="modal" v-show="visible">
    <div class="modal-mask" v-on:click.self="close"></div>
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <slot name="header"></slot>
          <uni-icons type="closeempty" size="14" @click="close"></uni-icons>
        </div>
        <div class="modal-body">
          <slot name="body"></slot>
        </div>
        <div class="modal-footer">
          <slot name="footer"></slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: {
    visible: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    close() {
      this.$emit("update:visible", false);
    },
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 9999;
  width: 100%;
  height: 100%;
}

.modal-mask {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.modal-dialog {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 80%;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
  transform: translate(-50%, -50%);
}

.modal-content {
  padding: 16px;
}

.modal-header {
  position: relative;
  padding-bottom: 10px;
  font-size: 18px;
  font-weight: bold;
}

.modal-header .modal-title {
  margin: 0;
}

.modal-close {
  position: absolute;
  top: 50%;
  right: 10px;
  font-size: 24px;
  font-weight: bold;
  color: #ccc;
  text-decoration: none;
  transform: translateY(-50%);
}

.modal-close:hover {
  color: #333;
}

.modal-body {
  padding: 10px 0;
  font-size: 16px;
  line-height: 1.5;
}

.modal-footer {
  padding-top: 10px;
  text-align: right;
  border-top: 1px solid #ccc;
}
</style>
