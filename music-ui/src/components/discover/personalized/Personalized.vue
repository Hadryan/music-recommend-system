<template>
  <div class="Personalized">
    <discover-individ></discover-individ>
    <div class="title" v-if="RecommendedSongList.length">
      推荐歌单
    </div>
    <musiclist
      :RecommendedSongList="RecommendedSongList"
      @songListDetails="songListDetails"
    ></musiclist>
    <div class="title">
      独家放送
    </div>
    <private-content></private-content>
    <div class="title">
      个性化推荐
    </div>
    <new-song></new-song>
  </div>
</template>

<script>
// 个性推荐
import discoverIndivid from "./individ/Individ";
import PrivateContent from "./individchildren/PrivateContent";
import NewSong from "./newsong/NewSong";
import Musiclist from "@/components/centent/musiclist/Musiclist";
// 请求路由
import { _getRecommendedSongList } from "@/network/discover/discover";
export default {
  data() {
    return {
      // 请求的条数
      limit: 12,
      // 推荐歌单列表
      RecommendedSongList: [],
      playlist: []
    };
  },
  methods: {
    // 获取推荐歌单列表
    async getRecommendedSongList() {},
    // 点击歌单后进入到详情歌单页面
    songListDetails(id) {
      console.log(id);
      this.$router.push({ path: "/home/musiclistdetail", query: { id } });
    }
  },
  mounted() {
    this.getRecommendedSongList();
  },
  components: {
    discoverIndivid,
    PrivateContent,
    NewSong,
    Musiclist
  }
};
</script>

<style lang="less" scoped>
.Personalized {
  .title {
    margin-top: 20px;
    font-size: 18px;
    border-bottom: 1px solid #ccc;
    padding-bottom: 5px;
    margin-bottom: 10px;
  }
}
</style>
