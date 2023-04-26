<template >
  <div style="background-color:white">
    <img :src="companylogo" class="logo">
    <div class="container" >
      <div class="" v-for="(item, index) in datares" :key="index" style="width:100%;display: flex;align-items: end;padding-bottom:15px;" :style="{ background: `${bgcolor[index]}` }">
        <ViewItems :item="item" :viewres="Mobileres"/>
      </div>
    </div>
  </div>
</template>
<script>
import ViewItems from './ViewItems'
export default{
  name:'MainComponentWeb',
  props: ['Mobileres'],
  components: {
    ViewItems
  },
  data(){
    return{
      companylogo:'',
      datares:{},
      bgcolor:["#3cb371","Orange","SlateBlue","Tomato","#ea4848","DeepSkyBlue"],
      windowHeight: 0,
    }
  },

  mounted() {
    let vm=this;
    fetch("https://krds-assignment.github.io/aoc/api-assets/data.json")
    .then(response => response.json())
    .then(data => {
      vm.companylogo=data.logo;
      vm.datares=data.features;
    //  console.log(data);
    });
  },
}
</script>
<style>
.logo{
  position:absolute;
  left:20px;
  height:20px;
  width:50px;
  top:20px
}
.childlogo{
  height: 30px;
  min-width: 30px;
}
.container {
  display: grid;
   grid-template-columns: 1fr 1fr 1fr;
   height: calc(100vh - 10px);
}
.column1 {
  float: left;
  width: 70%;
  height: 100%;
}
.column2 {
  width: 70%;
  height: 100%;
  text-align: right;

}
/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}
/*Design Title */
.title{
  color:white;
  text-transform:uppercase;
  font-weight: bold;
}
.borderbtm{
  border-bottom: 2px solid white;
  height: 2px;

}
.desc{
  color:white;
  text-transform:uppercase;
  
}
</style>
