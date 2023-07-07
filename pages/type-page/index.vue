<template>
  <view class="content">
    <!-- <view v-for="(item, index) in pageList" :key="index" class="li-box">
      <image class="logo" src="/static/logo.png"></image>
      <view class="title">名字</view>
    </view> -->
    <view class="left-sidebar">
      <view
        v-for="(item, index) in allList"
        :key="index"
        :class="['left-li', activeData.id === item.id && 'left-active']"
        @click="leftLiClick(item)"
      >
        <view>{{ item.name }}</view>
      </view>
    </view>
    <view class="right-box">
      <view
        v-for="(item, index) in rightData"
        :key="index"
        class="right-li"
        @click="showModalClick(item)"
      >
        <image class="right-img" src="/static/logo.png"></image>
        <view>{{ item.name }}</view>
      </view>
    </view>
    <u-modal
      :show="showModal"
      :title="detailData.name"
      :showConfirmButton="false"
      :closeOnClickOverlay="true"
	  @close="closeModel"
    >
      <view>
        <view class="modal-title">材料</view>
        <view>{{ detailData.material }}</view>
        <view class="modal-title">调料</view>
        <view>{{ detailData.seasoning }}</view>
        <view class="modal-title">步骤</view>
        <view
          v-for="(val, index) in detailData.step"
          :key="index"
          class="model-step"
          >{{ val }}</view
        >
      </view>
    </u-modal>
  </view>
</template>

<script>
import { AllList, RightData } from "./const";
export default {
  data() {
    return {
      allList: AllList,
      activeData: {},
      rightData: [],
      showModal: false,
      detailData: {},
    };
  },
  onLoad() {
    this.leftLiClick(AllList[0]);
  },
  methods: {
    leftLiClick(item) {
      this.activeData = item;
      this.rightData = RightData[item.id];
      console.log("this.rightData", this.rightData);
    },
    showModalClick(item) {
      this.detailData = item;
      this.showModal = true;
    },
	closeModel() {
		this.showModal = false
	}
  },
};
</script>

<style>
.content {
  display: flex;
  height: 100%;
}
.left-sidebar {
  width: 200rpx;
  height: 100%;
  font-size: 36rpx;
  color: #8f8f94;
  text-align: center;
  background: #f6f6f8;
}
.left-li {
  height: 40px;
  line-height: 40px;
  width: 100%;
}
.left-active {
  color: #fff;
  background: #3c3cd7;
}
.right-box {
  padding: 8rpx;
}
.right-li {
  text-align: center;
  padding: 4rpx;
}
.right-img {
  width: 100rpx;
  height: 100rpx;
}
.modal-title {
  font-size: 36rpx;
  display: block;
}
</style>
