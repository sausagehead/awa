<template>
  <div class="workoutbutton">
    <button @click="openPopUp">ADD</button>
  </div>
    <workoutpopup v-if="isPopUpVisible" @close="closePopUp">
      <h1>NAME</h1>
      <textarea v-model="textData" @keydown.enter="submitPopUp"></textarea>
      <button @click="submitPopUp" >submit</button>
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
.workoutbutton{
  display: flex;
  width: 100%;
  height: 20%;
  justify-content: flex-start;
  align-items: center;
}
.workoutbutton button{
  width: 100px;
  height: 100px;
}

</style>