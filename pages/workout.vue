<template>
  <div>
    <addworkout @submit="receiveText" />
    <button @click="saveText">SAVE</button>
    <div class="textBox" v-for="(item,index) in workarray" :key="index">
      <h1 >{{item.header}}</h1>
      <textarea v-model="item.text">{{item.text}}</textarea>
      <button @click="deleteItem(index)">deletebutton</button>
    </div>
  </div>


</template>

<script>
import addworkout from "@/components/addworkout.vue";
export default {
  name: 'Workout',
  // Component logic here
  components:{
    addworkout,
  },
  data(){
    return{
      workarray:[],
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
    deleteItem(index){
      this.workarray.splice(index,1);
      this.saveText();
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

<style >
</style>