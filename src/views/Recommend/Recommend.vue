<template>
  <div>
    <!-- 轮播图 -->
    <swiper></swiper>
    <!-- 推荐歌单 -->
    <play-list :recom-song-list='recomPlayList'></play-list>
    <!-- 推荐歌曲 -->
    <recommend-song :recom-song-list='recomSongList'></recommend-song>
    <!-- 推荐歌手 -->
    <recom-singer :recom-singer='recomSingerList'></recom-singer>
  </div>
</template>
<script>
//子组件
import Swiper from "@/components/Swiper/Swiper";
import PlayList from '@/components/RecommendPlaylist/PlayList'
import RecommendSong from '@/components/RecomendSong/RecommendSong'
import RecomSinger from '@/components/RecomSinger/RecomSinger'
//数据组件
import {getRecomPlayList,getRecomSongList,getRecomSingerList} from '../../network/recommed'
export default {
  data() {
    return {
      recomPlayList:[],
      recomSongList:[],
      recomSingerList:[]
    }
  },
  created(){
    this.getRecomPlayList(),
    this.getRecomSongList(),
    this.getRecomSingerList()

  },
  methods:{
    async getRecomPlayList(){
      const res = await getRecomPlayList()
      this.recomPlayList = res.result
      // console.log(res)
    },
     async getRecomSongList(){
      const res = await getRecomSongList()
      this.recomSongList = res.result
    },
     async getRecomSingerList(){
      const res = await getRecomSingerList()
      this.recomSingerList = res.artists
    },
  },
  components: {
    Swiper,
    PlayList,
    RecommendSong,
    RecomSinger
  }
};
</script>
<style lang="less" scoped>
</style>