<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <div class="support" v-if="seller.supports">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="text">{{seller.supports[0].description}}</span>
        </div>
      </div>
      <div v-if="seller.supports" class="support-count" @click="showDeatil">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper" v-on:click="showDeatil">
      <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
      <i class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img :src="seller.avatar" width="100%" height="100%">
    </div>
    <div class="detail" v-show="detailShow">
      <div class="detail-wrapper clearfix">
        <div class="detail-main"></div>
      </div>
      <div class="detail-close">
        <i class="icon-close"></i>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    data() {
      return {
        detailShow: false
      }
    },
    created() {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee'];
    },
    methods: {
      showDeatil() {
        debugger;
        this.detailShow = true
      }
    }
  };
</script>

<style lang="scss" rel="stylesheet/scss">
  @import "../../common/scss/minxi.scss";
  .header {
    position: relative;
    overflow: hidden;
    color: #fff;
    background: rgba(7, 17, 27, 0.5);
    .content-wrapper {
      position: relative;
      padding: 24px 12px 18px 24px;
      font-size: 0;
      .avatar {
        vertical-align: top;
        display: inline-block;
        img {
          border-radius: 2px;
        }
      }
      .content {
        display: inline-block;
        margin-left: 16px;
        .title {
          margin: 2px 0 8px 0;
          .brand {
            display: inline-block;
            vertical-align: top;
            width: 30px;
            height: 18px;
          @include bg-image('img/brand');
            background-size: 30px 18px;
            background-repeat: no-repeat;
          }
          .name {
            margin-left: 6px;
            font-size: 16px;
            line-height: 18px;
            font-weight: bold;
          }
        }
        .description {
          margin-bottom: 10px;
          line-height: 12px;
          font-size: 12px;
        }
        .support{
          .icon{
            display: inline-block;
            vertical-align: top;
            width: 12px;
            height: 12px;
            margin-right: 4px;
            background-size: 12px 12px;
            background-repeat: no-repeat;
            &.decrease{
             @include bg-image('img/decrease_1');
             }
            &.discount{
             @include bg-image('img/discount_1');
             }
            &.guarantee{
             @include bg-image('img/guarantee_1');
             }
            &.invoice{
             @include bg-image('img/invoice_1');
             }
            &.special{
             @include bg-image('img/special_1');
             }
          }
          .text{
            line-height: 12px;
            font-size: 10px;
          }
        }
      }
      .support-count{
        position: absolute;
        right: 12px;
        bottom: 14px;
        padding:0 8px;
        height: 24px;
        line-height: 24px;
        border-radius: 14px;
        background: rgba(0,0,0,.2);
        text-align: center;
        .count{
          vertical-align: top;
          font-size: 10px;
        }
        .icon-keyboard_arrow_right{
          margin-left: 2px;
          line-height: 24px;
          font-size: 10px;
        }
      }
    }
    .bulletin-wrapper{
      position: relative;
      height: 28px;
      line-height: 28px;
      padding:0 22px 0 12px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      background: rgba(7,17,27,.2);
      .bulletin-title{
        display: inline-block;
        vertical-align: top;
        margin-top:8px;
        width: 22px;
        height: 12px;
        @include bg-image('img/bulletin');
        background-size: 22px 12px;
        background-repeat: no-repeat;
      }
      .bulletin-text{
        vertical-align: top;
        margin:0 4px;
        font-size: 10px;
      }
      .icon-keyboard_arrow_right{
        position: absolute;
        font-size: 10px;
        right:12px;
        top:8px;
      }
    }
  .background{
    position: absolute;
    top:0;
    left:0;
    width: 100%;
    height: 100%;
    z-index: -1;
    filter: blur(10px);
  }
  .detail{
    position: fixed;
    top:0;
    left:0;
    z-index: 100;
    width:100%;
    height: 100%;
    overflow: auto;
    background: rgba(7,17,27,.8);
    .detail-wrapper{
      min-height: 100%;
      .detail-main{
        margin-top: 64px;
        padding-bottom: 64px;
      }
    }
    .detail-close{
      position: relative;
      height: 32px;
      width: 32px;
      margin: -64px auto 0 auto;
      clear: both;
      font-size: 32px;
    }
  }
  }
</style>
