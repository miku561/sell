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

        <a href="#" class="num-title" @click="showMask">
          <span>{{ classMap.length }}个</span>
          <i class="icon-keyboard_arrow_right"></i>
        </a>
        <div class="headerbg">
          <img :src="seller.avatar">
        </div>
      <div class="maskLayout" v-show="maskFlag" transition="fade">
        <div class="mask-wrap clearfix">
          <div class="mask-content">
            <p class="mask-title">{{ seller.name }}</p>
            <div class="mask-score">
              <star :size="48" :score="seller.score"></star>  
            </div>
            <div class="part-title">
              <div class="line"></div>
              <div class="title-name">优惠信息</div>
              <div class="line"></div>
            </div>
            <ul class="part-info" v-if="seller.supports">
              <li v-for="(val, index) in seller.supports" class="info-item">
                <span class="icon" :class="classMap[seller.supports[index].type]"></span>
                <span class="info-text">{{ seller.supports[index].description}}</span>
              </li>
            </ul>
             <div class="part-title">
              <div class="line"></div>
              <div class="title-name">商家公告</div>
              <div class="line"></div>
            </div>
            <div class="part-bulletin">
              <p class="text">{{ seller.bulletin }}</p>
            </div>
          </div>
        </div>
        <div class="mask-close" @click="showMask"><i class="icon-close"></i></div>
      </div>
    </div>  
</template>

<script>
  import star from '@/components/star/star'
  export default {
    props: {seller: {type: Object}},
    data () {
      return {
        maskFlag: false
      }
    },
    methods: {
      showMask () {
        this.maskFlag = !this.maskFlag
      }
    },
    created () {
      this.classMap = [ 'decrease', 'discount', 'special', 'invoice', 'guarantee' ]
    },
    components: {
      star
    }
  }
</script>

<style lang="scss" rel="stylesheet/scss">
  @import "../../common/sass/mixin.scss";
  .header{
    position: relative;
    overflow: hidden;
    background: rgba(7,17,27,0.5);
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
    .pub-ad{
        position:  relative;
        padding:0 22px 0 12px;
        height: 28px;
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
        line-height: 28px;
        font-size: 10px;
        background: rgba(7, 17, 27, 0.2);
        .ad-sign{
          display: inline-block;
          margin:0 4px 0 12px;
          width: 22px;
          height: 12px;
          vertical-align: text-bottom;
          @include bg-media(bulletin);
          background-repeat: no-repeat;
          background-size: 22px 12px;
        }
        i{
          position: absolute;
          top:8px;
          right: 12px;
          font-size: 10px;
        }
      }
    .num-title{
            position: absolute;
            right:16px;
            bottom:40px;
            padding:8px 10px;
            border-radius: 12px;
            line-height: 12px;
            font-size: 10px;
            color: #fff;
            background: rgba(0, 0, 0, 0.2);
            i{
              vertical-align: text-bottom;
            }
    }
    .headerbg{
      position: absolute;
      top:0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: -1;
      filter: blur(10px);
      img{
        width: 100%;
      }
    }
    .maskLayout{
      position: fixed;
      top: 0;
      left: 0;
      z-index: 100;
      width: 100%;
      height: 100%;
      overflow: auto;
      backdrop-filter:blur(10px);
      transition: all 4s;
      background: rgba(7,17,27,0.8);
      &.fade-transition{
        opacity: 1;
        background: rgba(7,17,27,0.8);
      }
      &.fade-enter,&.fade-leave{
        opacity: 0;
        background: rgba(7,17,27,1);
      }
      .mask-wrap{
        min-height: 100%;
        width: 100%;
        .mask-content{
          margin-top: 64px;
          padding-bottom: 64px;
          .mask-title{
            font-size: 16px;
            line-height: 16px;
            color: #fff;
            font-weight: 700;
            text-align: center;
          }
          .mask-score{
            padding: 16px 0 28px;
            text-align:center;
          }
          .part-title{
            display: flex;
            width: 80%;
            margin: 0 auto 24px ;
            .line{
              flex: 1;
              position: relative;
              top: -6px;
              border-bottom:1px solid rgba(255,255,255,0.2);
            }
            .title-name{
              padding: 0 12px;
              font-weight: 700;
            }
          }
          .part-info{
            width: 80%;
            margin: 0 auto 28px;
            .info-item{
              padding: 0 12px;
              margin-bottom: 12px;
              font-size: 0;
              &:last-child{
                margin-bottom: 0;
              }
              .icon{
                display: inline-block;
                margin-right: 6px;
                width: 16px;
                height: 16px;
                vertical-align: top;
                background-repeat: no-repeat;
                background-size: 16px 16px;
                &.decrease{
                  @include bg-media('decrease_2');
                }
                &.discount{
                  @include bg-media('discount_2');
                }
                &.guarantee{
                  @include bg-media('guarantee_2');
                }
                &.invoice{
                  @include bg-media('invoice_2');
                }
                &.special{
                  @include bg-media('special_2');
                }
              }
              .info-text{
                line-height: 16px;
                font-size: 12px;
              }
            }
          }
          .part-bulletin{
            margin: 0 auto;
            width: 80%;
            .text{
              padding: 0 12px;
              font-size: 12px;
              font-weight: 200;
              line-height: 24px;
            }
          }
        }
      }
      .mask-close{
          position: relative;
          margin: -64px auto 0 auto;
          width: 32px;
          height: 32px;
          font-size: 32px;
          clear: both;  
          color: rgba(255,255,255,0.5);
      }
    }
  }
  
</style>