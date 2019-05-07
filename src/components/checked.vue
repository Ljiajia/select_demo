<template>
<div> 
    <div>
        <h2>{{list.title}}</h2>
        <span :class="{cur:list.res.length===0}">不限</span> 
         <span v-for="(val,i) in list.cont" 
        :key="i"
        @click="addClass(i)"
        :class="{cur:list.res.find(item=>item.index===i)}"
        >{{val.title}}</span>
  </div> 
</div>
 
</template>

<script> 

export default {
    props:['list','index'],
   data() {
       return { 
       }
   },
   created() {
       window.xm=this;
   },
   methods: {
       addClass(i){ 
              this.list.cont[i].class=!this.list.cont[i].class; 
              this.$emit("addClass",{
                  index:i,
                  position:this.index,
                  text:this.list.cont[i].title,
                  type:this.list.type
              })
 
       }
   },
   components:{

   }
}
</script>

<style lang="scss">
    span{
        width: 100px;
        height: 30px;
        padding: 5px 10px;
        margin:0 5px;
        
    }
    span.cur{
            background: lime;
            color: #fff;
        }
</style>

