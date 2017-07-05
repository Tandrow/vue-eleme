<template>
  <div class="ratings">
    <div class="ratings-content">
      <div class="overview">
        <div class="overview-left">
          <h1 class="score">{{seller.score}}</h1>
          <div class="title">综合评分</div>
          <div class="rank">高于周边商家{{seller.rankRate}}</div>
        </div>
        <div class="overview-right">
          <div class="score-wrapper">
            <span class="title">服务态度</span>
            <star v-bind:size="36" v-bind:score="seller.serviceScore" class="star"></star>
            <span class="score">{{seller.serviceScore}}</span>
          </div>
          <div class="score-wrapper">
            <span class="title">商品评分</span>
            <star v-bind:size="36" v-bind:score="seller.foodScore"></star>
            <span class="score">{{seller.foodScore}}</span>
          </div>
          <div class="delivery-wrapper">
            <span class="title">送达时间</span>
            <span class="delivery">{{seller.deliveryTime}}分钟</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  import star from 'components/star/star'
  export default{
    props: {
      seller: {
        type: Object
      }
    },
    components: {
      star
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  .ratings
    position: absolute
    width: 100%
    left: 0
    .ratings-content
      .overview
        padding: 18px 0
        display: flex
        border-bottom: 1px solid rgba(7, 17, 27, 0.1)
        .overview-left
          flex: 0 0 137px
          text-align: center
          border-right: 1px solid rgba(7, 17, 27, 0.1)
          .score
            padding: 0
            margin: 0
            font-size: 24px
            color: rgb(255, 153, 0)
            line-height: 28px
          .title
            font-size: 12px
            margin-top: 6px
            color: rgb(7, 17, 27)
            line-height: 12px
          .rank
            font-size: 10px
            margin-top: 8px
            color: rgb(7, 17, 27)
            line-height: 10px
        .overview-right
          flex: 1
          margin: 0 auto
          padding: 0 0 0 24px
          .score-wrapper
            font-size: 0
            margin-bottom: 8px
            .title
              display: inline-block
              font-size: 12px
              color: rgb(7, 17, 27)
              line-height: 18px
              margin-right: 12px
            .star
              display: inline-block
            .score
              display: inline-block
              font-size: 12px
              margin-left: 12px
              color: rgb(255, 153, 0)
              line-height: 18px
          .delivery-wrapper
            font-size: 0
            .title
              font-size: 12px
              color: rgb(7, 17, 27)
              line-height: 18px
              margin-right: 12px
            .delivery
              font-size: 12px
              color: rgb(147, 153, 159)
              line-height: 18px
</style>
