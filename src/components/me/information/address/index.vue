<template>
  <div>
    <ul>
      <li>
        <div>
          <p>周必川</p>
          <p>火星省水星市地球村一号公寓</p>
        </div>
        <div>
          <img src=""
               alt="">
        </div>
      </li>
    </ul>
    <div>
      <img src=""
           alt="">
      <span>新增地址</span>
      <img src=""
           alt="">
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
export default {
  data () {
    return {
      opPage: {
        class: "address",
        header: true,
      }
    };
  },
  computed: {
    ...mapState('store_me_information_address_modules', ['meInformationAddressHeader'])
  },
  methods: {
    ...mapMutations({
      setInitPageConfig: 'INIT_PAGE_CONFIG'
    }),
    init () {
      let initPageConfig = {
        header: this.meInformationAddressHeader,
      }
      this.setInitPageConfig(initPageConfig)
    }
  },
  created () {
    this.init()
  }
};
</script>
<style lang='less' scoped>
ul{
  background:white;
  li{
  padding: 6px 15px;
}
}
</style>

