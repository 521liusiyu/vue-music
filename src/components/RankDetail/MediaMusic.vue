<template>
  <div class="mediamusic">
    <recom-title :title-name="title"></recom-title>
    <div class="media-music-item">
      <rank-item
        v-for="(item, index) in mediaList"
        :key="index"
        :rank-item="item"
      ></rank-item>
    </div>
  </div>
</template>
<script>
import RankItem from "@/components/RankDetail/RankItem";
import RecomTitle from "@/components/RecomTitle/RecomTitle";
export default {
  data() {
    return {
      title: "全球媒体榜"
    };
  },
  props: {
    mediaList: {
      type: Array
    }
  },
  components: {
    RecomTitle,
    RankItem
  }
};
</script>
<style lang="less" scoped>
.mediamusic{
    width: 1200px;
    height: 1000px;
    .media-music-item{
        margin: 10px 0 20px 10px;
        display: flex;
        flex: 1;
        flex-wrap: wrap;
    }
}
</style>