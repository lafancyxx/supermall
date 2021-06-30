<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>

    <div :style="activeStyle"><slot name="item-text"></slot></div>

    <!-- <div :class="{ active: isActive }"><slot name="item-text"></slot></div> -->
    <div class="text"><slot name="item-textt"></slot></div>
  </div>

  <!-- <div class="tab-bar-item">
    <img src="../../assets/img/home.svg" alt="" />
    <div>首页</div> -->

  <!-- <div class="tab-bar-item">
      <img src="../../assets/img/category.svg" alt="" />
      <div>分类</div>
    </div>
    <div class="tab-bar-item">
      <img src="../../assets/img/cart.svg" alt="" />
      <div>购物车</div>
    </div>
    <div class="tab-bar-item">
      <img src="../../assets/img/profile.svg" alt="" />
      <div>我的</div>
    </div> -->
  <!-- </div> -->
</template>

<script>
export default {
  name: "TabBaritem",
  props: {
    path: String,
    activeColor: {
      default: "pink",
      type: String,
    },
  },
  data() {
    return {
      // isActive: false,
    };
  },
  computed: {
    activeStyle() {
      return this.isActive ? { color: this.activeColor } : {};
    },
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1;
    },
  },
  methods: {
    itemClick() {
      this.$router.push(this.path).catch((error) => error);
    },
  },
};
</script>

<style scope>
.tab-bar-item {
  flex: 1;
  text-align: center;
  height: 48px;
  margin-top: 3px;
  font-size: 14px;
}
.tab-bar-item img {
  width: 24px;
  height: 24px;
  vertical-align: middle;
  margin-top: 5px;
}
.text {
  font-size: 12px;
  margin-top: 3px;
  color: #333;
}
</style>