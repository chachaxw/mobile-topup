<template>
  <view class="container">
    <uni-swiper-dot :info="info" :current="current" field="content" :mode="mode">
      <swiper class="swiper-box">
        <swiper-item v-for="(item, index) in info" :key="index">
          <view class="swiper-item">
            {{item.content}}
          </view>
        </swiper-item>
      </swiper>
    </uni-swiper-dot>
    <uni-search-bar :radius="22" placeholder="请输入手机号" @confirm="search" @input="input" v-model="value"></uni-search-bar>
    <text class="mobile-type">广东 电信</text>
    <view class="topup-list">
      <view :class="selected && item.id === selected.id ? 'topup-list-item active' : 'topup-list-item'"
        v-for="(item, index) in topupList" :key="index" @click="handleSelect(item)">
        <text class="price-text">
          {{item.price}}元
        </text>
        <text class="cost-text">
          售{{item.cost}}元
        </text>
      </view>
      <view class="topup-list-item">
        <text class="cost-text" style="font-size: 14px;" @click="handleMore">
          更多选项
        </text>
      </view>
    </view>
    <view>
      <button class="pay-button" type="default">¥50.00 立即充值</button>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        info: [{
          content: '内容 A'
        }, {
          content: '内容 B'
        }, {
          content: '内容 C'
        }],
        current: 0,
        mode: 'dot',
        value: '',
        topupList: [{
            id: 0,
            price: 30,
            cost: 29.9
          },
          {
            id: 1,
            price: 50,
            cost: 49.85
          },
          {
            id: 2,
            price: 100,
            cost: 98.00
          },
          {
            id: 3,
            price: 200.00,
            cost: 195.00
          },
          {
            id: 4,
            price: 300.00,
            cost: 290.00
          },
        ],
        selected: null
      }
    },
    methods: {
      search() {
        console.log("搜索");
      },

      input(e) {
        this.value = e.target.value;
      },

      handleSelect(item) {
        this.selected = item
      },

      handleMore() {
        console.log("展开更多");
      },

      handlePayment() {
        console.log("充值50元");
      }
    }
  }
</script>

<style lang="scss" scoped>
  .container {
    font-size: 14px;
    line-height: 24px;
  }

  .swiper-box {
    swiper-item {
      background-color: $uni-color-primary;
    }
  }

  .mobile-type {
    padding: 12px;
  }

  .topup-list {
    padding: 12px;
    display: flex;
    flex-wrap: wrap;

    .topup-list-item {
      width: 200rpx;
      height: 120rpx;
      margin-right: 12px;
      margin-bottom: 12px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      border: 1px solid $uni-border-color;
      border-radius: 8px;
      background-color: $uni-bg-color-hover;

      &.active {
        color: $uni-color-white;
        background-color: rgba($color: $uni-color-primary, $alpha: 0.8);
        
        .cost-text {
          color: inherit;
        }
      }
    }

    .price-text {
      font-weight: bold;
      font-size: 16px;
    }

    .cost-text {
      font-size: 12px;
      color: $uni-text-color-grey;
    }
  }

  .pay-button {
    width: 250px;
    color: white;
    border-radius: 22px;
    background-color: $uni-color-primary;
  }
</style>
