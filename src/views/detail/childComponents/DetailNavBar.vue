<template>
  <div>
    <nav-bar>
        <template #left>
          <img src="~assets/img/common/back.svg" alt="" class="back-img" @click="backClick">
        </template>
      <template #center>
        <div class="title">
          <div v-for="(item,index) in titles"
               class="title-item"
               :class="{active:currentIndex===index}"
               @click="itemClick(index)">{{item}}</div>
        </div>
      </template>
    </nav-bar>
  </div>
</template>

<script>
  import NavBar from "components/common/navbar/NavBar";

  export default {
    name: "DetailNavBar",
    components: {
      NavBar
    },
    data() {
      return {
        titles: ['商品', '参数', "评论", "推荐"],
        currentIndex:0
      }
    },
    methods:{
      itemClick(index){
        this.currentIndex=index;
        this.$emit("titleClick",index);
      },
      backClick(){
        this.$router.go(-1);
      }
    }
  }
</script>

<style scoped>
  .title {
    display: flex;
    font-size: 13px;
  }

  .title-item {
    flex-grow: 1;
  }
  .active{
    color: var(--color-high-text);
  }
  .back-img{
      margin-top: 11px;
  }
</style>