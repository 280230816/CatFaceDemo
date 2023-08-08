<template>
	<view class="content">
		<button @tap="openCamera">打开检测</button>
		<image :src="imageFace" style="width: 480rpx;height: 640rpx;"></image>
	</view>
</template>

<script>
	const catFace = uni.requireNativePlugin('wf-cat-face');
	export default {
		data() {
			return {
				faceData: {
					cameraId: '0', //0 是后置相机   1是前置相机
					quality: 80, //返回图片压缩比 默认80
					type: 0, //0 实时检测，15fps 返回一次，一秒大约是15fps，  1 检测1秒以上，选取一张图片返回并关闭页面
					num: 0, //1 是检测到后1s关闭相机并返回 对应检测到的图片  图片返回是base64格式的
				},
				imageFace: ""

			}
		},
		onLoad() {

		},
		methods: {
			openCamera() {
				let that = this;
				let index = 0;
				catFace.goToFace(this.faceData, (res) => {
					console.log('res==', res);
					that.imageFace = 'data:image/jpeg;base64,' + res.result
					if (index == 2) {
						catFace.closePage();
					}
					index++;
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>