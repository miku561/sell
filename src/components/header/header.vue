<template>
  <div class="header">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar">
      </div>
      <div class="sell-info">
        <p class="title">
          <span class="tag"></span>
          <span>{{ seller.name }}</span>
        </p>
        <p class="detail-info">
          {{ seller.description }} / {{ seller.deliveryTime }}分钟送达
        </p>
        <p v-if="seller.supports" class="reword-info">
          <span class="activity-signal" :class="classMap[seller.supports[0].type]"></span>
          <span class="reword-detail">{{ seller.supports[0].description }}</span>
        </p>
      </div>
      <div class="pub-ad">
        <span class="ad-sign"></span>
        <span>{{ seller.bulletin }}</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>

      <a href="#" class="num-title">
        <span>5个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </a>
  </div>  
</template>

<script>
  export default {
    props: {seller: {type: Object}},
    created () {
      this.classMap = [ 'decrease', 'discount', 'special', 'invoice', 'guarantee' ]
    }
  }
</script>

<style lang="scss" rel="stylesheet/scss">
  @import "../../common/sass/mixin.scss";
  .header{
    background: #889;
    color: #fff;
    .avatar{
      display: inline-block;
      margin: 24px 16px 18px 24px;
      vertical-align: top;
      img{
        border-radius: 2px;
      }
    }
    .sell-info{
      display: inline-block;
      margin-top: 25px;
      .title{
        font-size: 16px;
        .tag{
          display: inline-block;
          width: 30px;
          height: 18px;
          @include bg-media(brand);
          background-repeat: no-repeat;
          background-size: 30px 18px;
          vertical-align: sub;
        }
      }
      .detail-info{
        margin: 8px 0 10px;
        font-size: 12px;
      }
      .reword-info{
        .activity-signal{
          display: inline-block;
          margin-right: 4px;
          width: 12px;
          height: 12px;
          background-size: 12px 12px;
          background-repeat: no-repeat;
          vertical-align: middle;
          &.decrease{
            @include bg-media('decrease_1');
          }
          &.discount{
            @include bg-media('discount_1');
          }
          &.guarantee{
            @include bg-media('guarantee_1');
          }
          &.invoice{
            @include bg-media('invoice_1');
          }
          &.special{
            @include bg-media('special_1');
          }
        }
        .reword-detail{
          line-height: 12px;
          font-size: 10px;
        }
      }
    }
  }
</style>