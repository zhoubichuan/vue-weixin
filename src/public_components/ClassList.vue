<template>
  <div class="top">
    <ul>
      <li v-for="(item,index) in data "
          :key="index">
        <router-link :to="'/'+item.link">
          <img :src="require(`@/assets/image/address/${item.img ||'newFriends'}.png`)"
               alt>
          <p>{{item.title}}</p>
        </router-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data () {
    return {
      data: [
        { title: "新的朋友", img: "newFriends", link: "addressFriends" },
        { title: "群聊", img: "groupChat", link: "addressTalk" },
        { title: "标签", img: "tips", link: "addressTips" },
        { title: "公众号", img: "officialAcounts", link: "addressNumber" }
      ]
    };
  }
};
</script>
<style lang="less" scoped>
.top {
  ul {
    li {
      padding: 10px 15px;
      background-color: #ffffff;
      border-bottom: 1px solid #f2f2f2;
      img {
        width: 30px;
        height: 30px;
        display: inline-block;
      }
      p {
        display: inline-block;
        margin-left: 20px;
      }
    }
  }
}
</style>

