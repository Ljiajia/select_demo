<template>
  <div id="app"> 
    <div class="top">
       <p>已选择</p>
       <div v-for="(val,i) in data" :key="i">
        <div v-if="val.res.length">  
       <span v-for="(val,i) in val.res" :key="i">{{val.text}}</span>
       <span @click="remove(i)">X</span>
       </div>
       </div>
       
    </div>
  <div class="bottom">
     <checked v-for="(val,i) in data" 
     :key="i" :index="i"
      v-on:addClass="addClass" 
     :list="val"></checked>
  </div>
  </div>
</template> 
<script> 
import checked from "./components/checked";
import data from "./data/data.js";
export default {
   data() {
     return {
       data
     }
   }, 
   components:{
     checked
   },  
   methods: {
     addClass(obj){ 
       let {index,type,position,text}= obj;  
       let res=this.data[position].res; 
     let flag=res.findIndex(item=>item.index===index)
       if(flag==-1){
        if(type=='radio'){
                this.$set(res,'0',{index,text})
              }else{
                res.push(obj)
              }
       }else{ 
         res.splice(flag,1)
       } 
     },
     remove(i){ 
       this.data[i].res=[];
     
     }
   },
}
</script>

<style lang="scss">

</style>
