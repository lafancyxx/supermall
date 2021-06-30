<template>
  <div class="goodslist">
    <goods-listitem v-for="item in goods" :goodsitem="item" :key="item.index">
    </goods-listitem>
  </div>
</template>

<script>
import GoodsListitem from "../../content/goods/GoodsListitem.vue";
export default {
  name: "goodslist",
  props: {
    goods: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  components: {
    GoodsListitem,
  },
};
</script>

<style scoped>
.goodslist {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
</style>