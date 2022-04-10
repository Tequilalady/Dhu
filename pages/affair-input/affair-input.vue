<template>
	<view>
		<scroll-view :style="{height:wh-90+'px'}" style="width: 90%;margin: 5%;margin-top: 10px;margin-bottom: 0px;">
			<view :style="{height:wh-100+'px'}" style="background-color: #0000A0;color: #FFFFFF;border-radius: 25px;line-height: 30px;">
				<view style="margin-left: 30px;">
					<text style="font-size: 20px;font-weight: bold;">发布者</text>
					<view class="input"style="display: flex;align-items: center;">
					<view style="background-color: #00d7c3;color: #FFFFFF;width: 250px;font-size: 15px;height: 40px;display: flex;align-items: center;">
						<input type="text"value="" placeholder="输入姓名" confirm-type="done"cursor-spacing="3" style="text-align: left;"/>
					</view>
					</view>
				</view>
				<view style="margin-left: 30px;">
					<text style="font-size: 20px;font-weight: bold;">事务名称</text>
					<view class="input"style="display: flex;align-items: center;">
					<view style="background-color: #00d7c3;color: #FFFFFF;width: 250px;font-size: 15px;height: 40px;display: flex;align-items: center;">
						<input type="text"value="" placeholder="输入名称" confirm-type="done"cursor-spacing="3" style="text-align: left;"/>
					</view>
					</view>
				</view>
				<view style="margin-left: 30px;">
					<text style="font-size: 20px;font-weight: bold;">内容</text>
					<view class="input"style="display: flex;align-items: center;">
					<view style="background-color: #00d7c3;color: #FFFFFF;width: 250px;font-size: 15px;height: 160px;display: flex;align-items: center;">
						<textarea type="text"value="" placeholder="输入内容" confirm-type="done"cursor-spacing="3" style="text-align: left;"/>
					</view>
					</view>
				</view>
				<view style="margin-left: 30px;">
					<text style="font-size: 20px;font-weight: bold;">时间</text>
					<view style="display: flex;">
						<view style="background-color: #00d7c3;width: 100px;">
							<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
								<view style="item-algin:center;">{{date}}</view>
						 	</picker>
						</view>
						<view style="background-color: #00d7c3;width: 50px;">
							<picker mode="time" :value="time" start="00:00" end="23:59" @change="bindTimeChange">
								<view style="item-algin:center">{{time}}</view>
							</picker>
						</view>
					</view>
				</view>
				<view style="margin-left: 30px;">
					<text style="font-size: 20px;font-weight: bold;">地点</text>
					<view class="input"style="display: flex;align-items: center;">
					<view style="background-color: #00d7c3;color: #FFFFFF;width: 250px;font-size: 15px;height: 40px;display: flex;align-items: center;">
						<input type="text"value="" placeholder="输入地点" confirm-type="done"cursor-spacing="3" style="text-align: left;"/>
					</view>
					</view>
				</view>
			
			
			</view>
		</scroll-view>
		<button class="save" style="height: 80px;">保存</button>
	</view>	
</template>

<script>
	export default {
		data() {
			const currentDate=this.getDate(
			)
			const currentTime=this.getTime()
			return {
					wh:'',
					ww:'',
					date:currentDate,
					time:currentTime,
			}
		},
		 computed: {
		        startDate() {
		            return this.getDate('start');
		        },
		        endDate() {
		            return this.getDate('end');
		        }
		    },
		methods: {
			bindDateChange: function(e){
				this.date=e.detail.value
			},
			bindTimeChange: function(e){
				this.time=e.detail.value
			},
			getDate(type) {
			            const date = new Date;
			            let year = date.getFullYear();
			            let month = date.getMonth() + 1;
			            let day = date.getDate();
			
			            if (type === 'start') {
			                year = year - 60;
			            } else if (type === 'end') {
			                year = year + 2;
			            }
			            month = month > 9 ? month : '0' + month;
			            day = day > 9 ? day : '0' + day;
			            return `${year}-${month}-${day}`;
			        },
			getTime() {
				const time= new Date();
				let hour=time.getHours();
				let minutes=time.getMinutes();
				return `${hour}-${minutes}`
			}
		},
		onLoad() {
			const sysI=uni.getSystemInfoSync()
			this.wh=sysI.windowHeight
			this.ww=sysI.windowWidth
			console.log(this.time)
		}
		
	}
</script>

<style>
	.save{
		background-color: #0000A0;
		font-size: 40rpx;
		color: #FFFFFF;
		text-align: center;
	}
</style>
