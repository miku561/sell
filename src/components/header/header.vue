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
        <p v-if="seller.supports">
          <span class="activity-signal"></span>
          <span>{{ seller.supports[0].description }}</span>
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
    props: {seller: {type: Object}}
  }
</script>

<style rel="stylesheet/scss">
  .header{
    
  }
</style>