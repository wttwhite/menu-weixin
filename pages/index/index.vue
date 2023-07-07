<template>
  <view class="content">
   首页
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
