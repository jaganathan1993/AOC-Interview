<template >
  <div >
      <img :src="companylogo" class="logo" style="position:absolute;z-index:9999;padding:4px 4px">
      <carousel :items-to-show="1.5" v-bind="settings" >
        <slide class="" v-for="(item, index) in datares" :key="index" style="width:100%;display: flex;align-items: end;padding-bottom:15px;" :style="{ background: `${bgcolor[index]}` }">
          <ViewItems :item="item" :viewres="Mobileres"/>
        </slide>
        <template #addons>
          <navigation />
          <pagination />
        </template>
      </carousel>
  </div>
</template>
<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import ViewItems from './ViewItems';
export default{
  name:'MainComponentMobile',
  props: ['Mobileres'],
  components: {
    ViewItems,
    Carousel,
    Slide,
    Pagination,
    Navigation,
 },
  data(){
    return{
      companylogo:'',
      datares:{},
      bgcolor:["#3cb371","Orange","SlateBlue","Tomato","#ea4848","DeepSkyBlue"],
      settings: {
        itemsToShow: 1,
        snapAlign: 'center',
      },
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
  left:20px;
  height:20px;
  width:50px;
  color:black;

}
.childlogo{
  height: 50px;
  min-width: 50px;
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
}
.borderbtm{
  border-bottom: 2px solid white;
  height: 2px;

}
.desc{
  color:white;
  text-transform:uppercase;

}
.carousel__slide {
  padding: 10px;
}
.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  color:white;
}
</style>
