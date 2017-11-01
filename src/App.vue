<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
       <router-link to="/goods">商品</router-link>    
     </div>
      <div class="tab-item">
       <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view> </router-view>
  </div>
</template>

<script>
  import header from '@/components/header/header'
  import axios from 'axios'
  export default {
    data () {
      return {
        seller: {},
        goods: {},
        ratings: {}
      }
    },
    components: {
      'v-header': header
    },
    created () {
      axios.get('static/data.json').then(res => {
        this.seller = res.data.seller
      })
    }
  }
</script>

<style lang="scss">
   @import "./common/sass/mixin.scss";
   .tab{
    display: flex;
    // @include border1px(rgba(70, 85, 93, 0.1));
    width: 100%;
    height: 40px;
    line-height: 40px;
    .tab-item{
      flex: 1;
      text-align: center;
      & > a{
        display: block;
        font-size: 14px;
        color: rgb(77, 85, 93);
        &.active{
          color: rgb(240, 20, 20);
        }
      }
    }
  }
</style>

