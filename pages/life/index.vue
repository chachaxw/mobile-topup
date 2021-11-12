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
    <uni-search-bar :radius="22" placeholder="查找" @confirm="search" @input="input" v-model="value"></uni-search-bar>
    <view class="category-wrapper">
      <scroll-view class="category-list">
        <view :class="item.value === selected ? 'category-list-item active' : 'category-list-item'"
          v-for="(item, index) in categoryList" :key="index" @click="handleSelect(item)">
          {{item.label}}
        </view>
      </scroll-view>
      <scroll-view class="category-content">
        <view class="product-item" v-for="(item, index) in productList" :key="index">
          <image class="product-icon"></image>
          <text>{{item.label}}</text>
        </view>
      </scroll-view>
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
        selected: 'video',
        categoryList: [{
            label: '视频会员',
            value: 'video'
          },
          {
            label: '文娱会员',
            value: 'entertainment'
          },
          {
            label: '生活服务',
            value: 'life'
          },
          {
            label: '虚拟卡币',
            value: 'coin'
          },
          {
            label: '网游会员',
            value: 'game'
          },
        ],
        productList: [{
            label: 'PPTV视频',
            value: 'pptv'
          },
          {
            label: '人人视频',
            value: 'renren'
          },
          {
            label: '爱奇艺',
            value: 'aiqiyi'
          },
          {
            label: '埋堆堆',
            value: 'maiduidui'
          },
          {
            label: '1905电影网',
            value: '1905'
          },
          {
            label: '南瓜',
            value: 'nangua'
          },
          {
            label: '腾讯视频',
            value: 'Tencent'
          },
          {
            label: '优酷',
            value: 'youku'
          },
          {
            label: '芒果TV',
            value: 'mangguo'
          },
        ],
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
        this.selected = item.value
      },
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

  .category-wrapper {
    display: flex;
    height: calc(100vh - 206px);

    .category-list {
      max-width: 96px;
      min-width: 96px;
      height: 100%;
      text-align: center;
      background-color: $uni-bg-color-grey;

      &-item {
        padding: 12px 0;

        &.active {
          color: $uni-color-primary;
          background-color: $uni-color-white;
        }
      }
    }

    .category-content {
      height: 100%;
      flex: 1 auto;
      display: flex;
      flex-wrap: wrap;

      .product-item {
        width: 33.3%;
        margin-bottom: 16rpx;
        display: inline-flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        image {
          width: 120rpx;
          height: 120rpx;
          margin-bottom: 6rpx;
          border-radius: $uni-border-radius-base;
          background-color: $uni-bg-color-grey;
        }
        
        text {
          font-size: 12px;
        }
      }
    }
  }
</style>
