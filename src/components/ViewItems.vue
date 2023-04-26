<template>
  <div v-if="viewres ==1">
    <div class="row" style="display: flex;    align-items: center;text-align:left;width:100%" >
      <div class="column1" style="padding-left:2%;justify-content:flex-end;">
        <img :src="item.logo" class="childlogo"/>
        <p class="title" style="width:280px;font-size:22px;">{{ item.title }}</p>
        <p class="borderbtm"></p>
        <p class="desc">{{ item.desc }}</p>
      </div>
    </div>
    <div class="row" style="display: flex;    align-items: center;text-align:left;width:100%" >
      <div class="column2">
        <img :src="item.image" style="max-width:100%;max-height:100%;text-align: right;padding:15px"/>
      </div>
  </div>
  </div>
  <div v-else>
    <div class="row" style="display: flex;    align-items: center;text-align:left;width:100%" >
      <div class="column1" style="padding-left:10%;justify-content:flex-end;">
        <img :src="item.logo" class="childlogo"/>
        <p class="title" style="width:200px;">{{ item.title }}</p>
        <p class="borderbtm"></p>
        <p class="desc">{{ item.desc }}</p>
      </div>
      <div class="column2">
        <img :src="item.image" style="max-width:70%;max-height:90%;text-align: right;padding:15px"/>
      </div>
  </div>

  </div>
</template>
<script>
  export default{
    name:"ViewItems",
    props: ['item','viewres']
  }
</script>
