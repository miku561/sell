<template>
  <div class="header">
    <div class="wraper">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar">
      </div>
      <div class="sell-info">
        <p>
          <span class="tag"></span>
          <span>{{ seller.name }}</span>
        </p>
        <p>
          {{ seller.description }}/{{ seller.deliveryTime }}分钟送达
        </p>
        <p>
          <span class="activity-signal"></span>
          <span>{{ seller.supports.description }}</span>
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
  </div>  
</template>

<script>
  export default {
    data: {
      activeObj: ['在线支付满28减5', 'VC无限橙果汁全场8折', '单人精彩套餐', '该商家支持发票,请下单写好发票抬头', '已加入“外卖保”计划,食品安全保障']
    },
    props: {seller: {type: Object}}
  }
</script>

<style rel="stylesheet/scss">
  .header{
    
  }
</style>