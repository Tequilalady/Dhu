<template>
	<view class="content">
		<view class="Plate">
			<view class="sign"> <!--布局遮罩-->
				<text class="sign-text">Tomorrow stars today!</text>
			</view>
			<text class="title">{{title}}</text>
		</view>
		<view class="Button-title" style="margin-top: 20rpx;margin-left: 20rpx;">Daily</view> <!--按钮区标题-->
		<view class="button-area">
			<button class="status-input" @click="goto('/pages/status-input/status-input')">status</button>
			<button class="group-input"@click="goto('/pages/kpi-input/kpi-input')">groups</button>
			<button class="affair-input"@click="goto('/pages/affair-input/affair-input')">affair</button>	
			<button class="activities-input"@click="goto('/pages/acti-input/acti-input')">activity</button>
		</view>
		<view class="Acti-title" style="margin-bottom:10px;margin-left: 20rpx;">Events</view> <!--活动区标题-->
		<view class="post-area" style="height: 300px;"> <!--活动展示区 -->
			<view class="post-1" style="border-radius: 25rpx;background-color: #ffffff;width: 90%;">
				<view class="post-content">
					<view class="acti-1">
						<view>
							<uni-icons type="calendar" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 35rpx;">{{date}}</text>
						</view> <!--活动时间 -->
						<view>
							<uni-icons type="map" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 40rpx;">{{place}}</text>
						</view> <!--活动地点 -->
						<text class="act-info" style="font-size: 30rpx;">{{information}}</text> <!--活动概要 -->
					</view>
					<view class="acti-2" style="width: 100px;height: 65px;margin-left: 30rpx;">
						<button type="primary" size="default" style="margin: 10px;" @click="goto('/pages/')">详细</button>	
					</view>
				</view>
			</view>
			<view class="post-1" style="border-radius: 25rpx;background-color: #ffffff;width: 90%;">
				<view class="post-content">
					<view class="acti-1">
						<view>
							<uni-icons type="calendar" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 35rpx;">{{date}}</text>
						</view> <!--活动时间 -->
						<view>
							<uni-icons type="map" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 40rpx;">{{place}}</text>
						</view> <!--活动地点 -->
						<text class="act-info" style="font-size: 30rpx;">{{information}}</text> <!--活动概要 -->
					</view>
					<view class="acti-2" style="width: 100px;height: 65px;margin-left: 30rpx;">
						<button type="primary" size="default" style="margin: 10px;">详细</button>		
					</view>
				</view>
			</view>
			<view class="post-1" style="border-radius: 25rpx;background-color: #ffffff;width: 90%;">
				<view class="post-content">
					<view class="acti-1">
						<view>
							<uni-icons type="calendar" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 35rpx;">{{date}}</text>
						</view> <!--活动时间 -->
						<view>
							<uni-icons type="map" size="21" color="#0000a0"></uni-icons>
							<text style="font-size: 40rpx;">{{place}}</text>
						</view> <!--活动地点 -->
						<text class="act-info" style="font-size: 30rpx;">{{information}}</text> <!--活动概要 -->
					</view>
					<view class="acti-2" style="width: 100px;height: 65px;margin-left: 30rpx;">
						<button type="primary" size="default" style="margin: 10px;">详细</button>		
					</view>
				</view>
			</view>
		</view>
	</view>
	
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				date: '2022/2/22',
				place: 'somewhere',
				information:'安全小组沟通'
			}
		},
		onLoad() {

		},
		methods: {
			goto(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		
	}
	
	.sign {
		height: 80rpx;
		width: 100%;
		background-color: #0000a0;
	}
	.sign-text {
		color: #ffffff;
		font-size: 50rpx;
		display: flex;
		margin-left: 20rpx;
	}

	.Plate {
		height: 400rpx;
		width: 100%;
		background-color: #0000a0;
		border-radius: 50rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	
	.Button-title{
		font-size: 50rpx;
		color: #0000A0;
	}
	
	.button-area{
		display: flex;
	}
	
	.button-area view{
		width: 25%;
		height: 200rpx;
		background-color: #e6e6e6;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
	.button-area button{
		width: 150rpx;
		height:150rpx;
		border-radius: 25rpx;
		background-color: #0000A0;
		font-size: 30rpx;
		color: #FFFFFF;
	}
	
	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	
	.post-area{
		display: flex;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		margin: 20rpx;
	}
	
	.post-1{
		margin: 10px;
	}
	
	.post-content{
		margin: 10px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	
	page{
		background-color: #e6e6e6;
	}
	
	.Acti-title{
		font-size: 50rpx;
		color: #0000A0;
	}
</style>
