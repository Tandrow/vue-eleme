<template>
  <div id="app">
    <v-header v-bind:seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评价</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view v-bind:seller="seller"></router-view>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from 'components/header/header'
  import { ERR_OK } from 'common/js/config'

  export default {
    name: 'app',

    data() {
      return {
        seller: {}
      }
    },

    created() {
      this._getHeader()
    },

    methods: {
      _getHeader() {
        this.$http.get('/api/seller').then((res) => {
          res = res.body
          if (res.errno === ERR_OK) {
            this.seller = Object.assign({}, this.seller, res.data)
          }
        })
      }
    },

    components: {
      'v-header': header
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "common/stylus/mixin.styl"
  #app
    padding: 0
    margin: 0
    .tab
      display: flex
      height: 40px
      line-height 40px
      width: 100%
      border-1px(rgba(7, 17, 27, 0.1))
      .tab-item
        flex: 1
        text-align center
        & > a
          display: block
          font-size: 14px
          color: rgb(77, 85, 93)
          &.active
            color: rgb(240, 20, 20)
</style>
