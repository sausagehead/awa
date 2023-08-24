<template>
  <div class="workoutbutton">
    <mybutton @click="openPopUp">ADD</mybutton>
  </div>
    <workoutpopup v-if="isPopUpVisible" @close="closePopUp">
      <h1>NAME</h1>
      <textarea v-model="textData" @keydown.enter="submitPopUp"></textarea>
      <mybutton @click="submitPopUp" >submit</mybutton>
    </workoutpopup>

</template>

<script>
import workoutpopup from "@/components/workoutpopup.vue";
export default{
  components:{
    workoutpopup
  },
  data() {

    return {
      textData : "",
      isPopUpVisible: false
    };
  },
  methods:{
    openPopUp(){
      this.isPopUpVisible=true;
    },
    closePopUp(){
      this.isPopUpVisible=false;
    },
    submitPopUp(){
      this.$emit('submit',this.textData);
      this.isPopUpVisible=false;
      this.textData=""
    }
  },
};
</script>

<style scoped>
h1{
  display:flex;
  justify-content: center;
  align-items: center;
  background-color: black;
  color: white;
  border: 2px solid #1A1A1A;
  border-radius: 15px;
  box-sizing: border-box;
}
textarea{
  display:flex;
  justify-content: center;
  align-items: center;
  margin: 20px;
}
.workoutbutton {
  margin: 10px;
}


</style>