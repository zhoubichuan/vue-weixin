<template>
  <div class="people">
    <ul>
      <li @click="handleClick"
          v-for="(item,key) in peopleList"
          :key="key">
        <router-link :to="'/messagePeople:'+item.title">
          <div class="left">
            <img class="photo"
                 :src="require(`@/assets/image/message/${item.photo||p1}.svg`)"
                 alt>
            <div class="message">
              <p class="message-title">{{item.title}}</p>
              <p class="message-information">{{item.tips}}</p>
            </div>
          </div>
          <div class="message-time">{{item.time}}</div>
        </router-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data () {
    return {
      peopleList: ""
    };
  },
  created () {
    let url = this.$requestUrl.message.peopleList
    this.$axios.get(url).then(res => {
      if (res.data.code == 200) {
        this.peopleList = res.data.message;
      }
    });
  },
  methods: {
    handleClick (e) {
      this.informationIsShow = !this.informationIsShow;
      let url = this.$requestUrl.message.peopleDetail
      this.$axios.get(url).then(res => {
        if (res.data.code == 200) {
          this.peopleList = res.data.message;
        }
      });
    }
  }
};
</script>
<style lang="less" scoped>
.people {
  ul {
    background-color: white;
    padding: 0 10px;
    li {
      padding: 5px 0;
      background-color: #ffffff;
      border-bottom: 1px solid #f2f2f2;
      a {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        .left {
          display: flex;
          flex-direction: rew;
          .photo {
            width: 40px;
            height: 40px;
          }
          .message {
            padding-left: 10px;
            .message-information {
              color: gray;
            }
          }
        }
        .message-time {
          float: right;
          color: gray;
        }
      }
    }
    li:last-child {
      border: none;
    }
  }
}
</style>


