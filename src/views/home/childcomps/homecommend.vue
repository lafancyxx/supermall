<template>
  <div class="homerecommends">
    <div class="recommends-item" v-for="item in recommends" :key="item.index">
      <a :href="item.link"><img :src="item.image" alt="" /></a>
      <div>{{ item.title }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "homecommend",

  props: {
    recommends: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style>
.homerecommends {
  display: flex;

  text-align: center;
  font-size: 14px;
  padding: 15px 0px 10px;
  border-bottom: 8px solid rgb(208, 207, 207);
}
.recommend-item {
  flex: 1;
}
.recommends-item img {
  width: 80px;
  padding: 0px 5px;
  height: 80px;
  width: 100%;
  margin-bottom: 10px;
}
</style>