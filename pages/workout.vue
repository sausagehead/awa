<template>
  <div class="workout-page">
    <addworkout @submit="receiveText"  />
    <div class="saveAndDelete-menu">
    <mybutton @click="saveText">SAVE</mybutton>
    <mybutton @click="showDeleteMenu">DELETEMENU</mybutton>
    </div>
    <div class="delete-menu-popup" v-if="deleteMenuVisible">
      <div class="delete-menu">
        <div class="menu-item" v-for="(item,index) in workarray" :key="index">
          <label>
            <input type="checkbox" v-model="selectedItems" :value="index" />
            {{ item.header }}
          </label>
        </div>
        <mybutton @click="confirmDelete">delete</mybutton>
      </div>
    </div>
    <div class="textBox" v-for="(item,index) in workarray" :key="index">
      <h1 >{{item.header}}</h1>
      <textarea v-model="item.text">{{item.text}}</textarea>
    </div>
  </div>


</template>

<script>
import addworkout from "@/components/addworkout.vue";
import workoutpopup from "@/components/workoutpopup.vue";
export default {
  name: 'Workout',
  // Component logic here
  components:{
    addworkout,
  },
  data(){
    return{
      workarray:[],
      deleteMenuVisible:false,
      selectedItems : [],
      }
    },
  methods:{
    receiveText(data){
      const work = {
        header : "",
        text : "",
      };
      this.textData=data;
      this.workarray.push({header: data,text:''});

      localStorage.setItem('textyworkout',JSON.stringify(this.workarray))
    },
    saveText(){
      localStorage.setItem('textyworkout', JSON.stringify(this.workarray));
    },
    showDeleteMenu(){
    this.deleteMenuVisible=true;
    },
    confirmDelete(){
      this.selectedItems.sort((a, b) => b - a);
      for(const index of this.selectedItems){
        this.workarray.splice(index,1)
      }
      this.selectedItems=[];
      this.saveText();
      this.deleteMenuVisible=false;
    }
  },

  created() {
    if(process.client){
      const localData = JSON.parse(localStorage.getItem('textyworkout'));
      if (localData) {
        this.workarray = localData;
      }
    }
    }
};


</script>

<style scoped >
.delete-menu-popup {
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
.delete-menu {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.2);
}
.textBox{
  display:flex;
  flex-direction: row;
}
.textBox h1{
  display:flex;
  justify-content: center;
  align-items: center;
  background-color: black;
  color: white;
  border: 2px solid #1A1A1A;
  box-sizing: border-box;
}
.saveAndDelete-menu{
  display:flex;
  justify-content: center;
  margin: 10px;
}
</style>