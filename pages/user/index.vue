<template>
	<view class="container">
    <view class="card user-profile">
      <image class="avatar"></image>
      <view>
        <view class="username">Krewwwcn</view>
        <view class="point">我的积分: 0</view>
      </view>
    </view>
    <view class="card my-order">
      <text class="title">我的订单</text>
      <view class="list">
        <view class="list-item">
          <image src="../../static/history.png"></image>
          <text>全部</text>
        </view>
        <view class="list-item">
          <image src="../../static/creditcard.png"></image>
          <text>待付款</text>
        </view>
        <view class="list-item">
          <image src="../../static/success.png"></image>
          <text>已完成</text>
        </view>
      </view>
    </view>
    <view class="card my-coupon">
      <text class="title">我的资产</text>
      <view class="list">
        <view class="list-item">
          <text>0张</text>
          <text>代金券</text>
        </view>
      </view>
    </view>
    <view class="card service" style="margin-top: 12px;">
      <view class="list-item">
        <image src="../../static/service.png"></image>
        <text>客服电话</text>
      </view>
      <view class="list-item">
        <image src="../../static/help.png"></image>
        <text>客服电话</text>
      </view>
    </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui'
			}
		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	.container {
    height: 100vh;
		padding: 12px;
		font-size: 14px;
    box-sizing: border-box;
    background-color: $uni-bg-color-grey;
	}
  
  .card {
    padding: 12px;
    border-radius: $uni-border-radius-lg;
    background-color: $uni-color-white;
    
    .title {
      display: block;
      color: $uni-color-subtitle;
      padding: 0 0 12px;
      border-bottom: 1rpx solid $uni-border-color;
    }
  }
  
  .user-profile {
    display: flex;
    align-items: center;
    
    .avatar {
      width: 144rpx;
      height: 144rpx;
      border-radius: $uni-border-radius-circle;
      background-color: $uni-bg-color-grey;
    }
    
    .username {
      font-size: 16px;
      font-weight: bold;
    }
    
    .point {
      color: $uni-color-subtitle;
    }
    
    >view {
      flex: 1 auto;
      padding-left: 16px;
    }
  }
  
  .list {
    margin-top: 12px;
    display: flex;
    justify-content: space-around;
  }
  
  .list-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    color: $uni-text-color;
    
    image {
      width: 32px;
      height: 32px;
    }
  }
  
  .my-order,
  .my-coupon,
  .service {
    margin-top: 12px;
  }
  
  .my-coupon .list {
    justify-content: flex-start;
  }
  
  .service {
    padding: 0 12px;

    .list-item {
      padding: 12px 0;
      flex-direction: row;
      justify-content: flex-start;
      
      &:not(:last-child) {
        border-bottom: 1rpx solid $uni-border-color;
      }
      
      image {
        width: 18px;
        height: 18px;
      }
    }
  }
</style>
