<template>
  <div>
   <nav-bar class="home-nav">
     <div slot="center">购物街</div>
   </nav-bar>
   <home-swiper :zbanners="banners"></home-swiper> 
   <recommend-view :zrecommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar';
import {getMultiData} from 'network/home';
import HomeSwiper from './childComps/HomeSwiper';
import RecommendView from './childComps/RecommendView'


export default {
  name: "Home",
  components:{
    NavBar,
    HomeSwiper,
    RecommendView
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    getMultiData().then(res =>{
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list

    })
  }
}
</script>

<style scoped>
.home-nav{
  background:rgb(250, 115, 160);
  color: #ffffff;
}
</style>
