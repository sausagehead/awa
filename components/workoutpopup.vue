<template>
<div class="popup">
  <div class="popup-content">
    <slot></slot>
    <div class="button-box">
      <mybutton @click="ClosePopUp">close</mybutton>
    </div>
  </div>
</div>
</template>
<script>
export default{
  methods:{
    ClosePopUp(){
this.$emit('close');
    }
  },
};
</script>

<style scoped>
.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup-content {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.2);
}

</style>