<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <homecommend :recommends="recommends"></homecommend>
    <feature-view> </feature-view>
    <tab-control
      class="tab-control"
      :titles="['流行', '新款', '折扣']"
      @tabClick="tabClick"
    />
    <goods-list :goods="showgoods"> </goods-list>

    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
    <div>a</div>
  </div>
</template>

<script>
import NavBar from "../../components/common/navbar/NavBar.vue";
import HomeSwiper from "./childcomps/HomeSwiper.vue";
import { gethomemultidata } from "network/home";
import { gethomegoods } from "network/home";
import { Swiper, SwiperItem } from "../../components/common/swiper";
import Homecommend from "./childcomps/homecommend.vue";
import FeatureView from "./childcomps/FeatureView.vue";
import TabControl from "../../components/content/tabcontrol/TabControl.vue";
import GoodsList from "../../components/content/goods/GoodsList.vue";
import GoodsListitem from "../../components/content/goods/GoodsListitem.vue";

export default {
  name: "home",
  components: {
    NavBar,
    Swiper,
    SwiperItem,
    HomeSwiper,
    Homecommend,
    FeatureView,
    TabControl,
    GoodsList,
    GoodsListitem,
    SwiperItem,
    Swiper,
  },
  methods: {
    tabClick(index) {
      switch (index) {
        case 0:
          this.currenttype = "pop";
          break;
        case 1:
          this.currenttype = "new";
          break;
        case 2:
          this.currenttype = "sell";
          break;
      }
      console.log(index);
    },
    gethomemultidata() {
      gethomemultidata().then((res) => {
        console.log(res);
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    gethomegoods(type) {
      const page = this.goods[type].page + 1;
      gethomegoods(type, page).then((res) => {
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page += 1;
      });
    },
  },
  computed: {
    showgoods() {
      return this.goods[this.currenttype].list;
    },
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        new: { page: 0, list: [] },
        sell: { page: 0, list: [] },
      },
      currenttype: "pop",
    };
  },
  created() {
    this.gethomemultidata();
    this.gethomegoods("pop", 1);
    this.gethomegoods("sell", 1);
    this.gethomegoods("new", 1);
  },
};
</script>

<style scoped>
.home-nav {
  position: sticky;
  background-color: var(--color-tint);
  color: aliceblue;
  left: 0;
  right: 0;
  top: 0;
}
.tab-control {
  position: sticky;
  top: 40px;
  z-index: 10;
}
</style>