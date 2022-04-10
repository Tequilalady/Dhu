<template>
	<view>
		<view class="sroll-container">
			<!-- 区域选择 -->
			<scroll-view class="moulding" scroll-y="true" :style="{height: wh+'px'}" style="width: 100px;">
				<block v-for="(item,i) in arealist " :key='i'>
					<view :class="['moulding-view', active===i ? 'active' : '']" @click="sclect(i)"><text style="margin-top:40px;color: #0000A0;">{{item.area}}</text></view>
				</block>
			</scroll-view>
			<!-- 内容填写区 -->
			<scroll-view class="input" scroll-y="true" :style="{width: ww+'px'}"> 
				<block>
					<view class="input-md1":style="{height:wh-40+'px'}" style="line-height:40px;background-color: #0000A0;margin-top: 20px;margin-bottom: 20px;border-radius: 10px;">
						<form  @submit="formSubmit" @reset="formReset">
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">质量</text>
								<radio-group name="radio" style="line-height: 40px;">
									<label style="margin: 10px;">
										<radio value="radio1" checked="true"/><text style="color: #FFFFFF;margin: 10rpx;">正常</text>
									</label>
									<label style="margin: 10px;">
										<radio value="radio2" /><text style="color: #FFFFFF;margin: 10rpx;">发生事件</text>
									</label>
								</radio-group>
							</view>
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">效率</text>
								<view style="display: flex;align-items: center;">
									<radio-group name="radio" style="line-height: 40px;width: 220px;">
										<label style="margin: 10px;">
											<radio value="radio1" checked="true" /><text style="color: #FFFFFF;margin: 10rpx;">正常</text>
										</label>
										<label style="margin: 10px;">
											<radio value="radio2" /><text style="color: #FFFFFF;margin: 10rpx;">发生事件</text>
										</label>
									</radio-group>
									<view class="time-input"style="display: flex;align-items: center;">
										<view style="background-color: #00d7c3;color: #FFFFFF;width: 40px;font-size: 20px;height: 40px;display: flex;align-items: center;">
											<input type="text"value="" placeholder="____" confirm-type="done" maxlength="3" cursor-spacing="3" style="text-align: center;"/>
										</view>
										<text style="color: #FFFFFF;background-color: #00d7c3;width: 15px;font-size: 15px;">H</text>
									</view>
								</view>
							</view>
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">安全</text>
								<view style="display: flex;align-items: center;">
									<radio-group name="radio" style="line-height: 40px;width: 220px;">
										<label style="margin: 10px;">
											<radio value="radio1" checked="true" /><text style="color: #FFFFFF;margin: 10rpx;">正常</text>
										</label>
										<label style="margin: 10px;">
											<radio value="radio2" /><text style="color: #FFFFFF;margin: 10rpx;">发生事件</text>
										</label>
									</radio-group>
								</view>							
							</view>
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">食品安全</text>
								<view style="display: flex;align-items: center;">
									<radio-group name="radio" style="line-height: 40px;width: 220px;">
										<label style="margin: 10px;">
											<radio value="radio1" checked="true"/><text style="color: #FFFFFF;margin: 10rpx;">正常</text>
										</label>
										<label style="margin: 10px;">
											<radio value="radio2" /><text style="color: #FFFFFF;margin: 10rpx;">发生事件</text>
										</label>
									</radio-group>
								</view>							
							</view>
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">超耗</text>
								<view style="display: flex;align-items: center;">
									<radio-group name="radio" style="line-height: 40px;width: 220px;">
										<label style="margin: 10px;">
											<radio value="radio1" checked="true"/><text style="color: #FFFFFF;margin: 10rpx;">正常</text>
										</label>
										<label style="margin: 10px;">
											<radio value="radio1"/><text style="color: #FFFFFF;margin: 10rpx;">产生返工</text>
										</label>
									</radio-group>
									<view class="Wasted-input"style="display: flex;align-items: center;">
										<view style="background-color: #00d7c3;color: #FFFFFF;width: 40px;font-size: 20px;height: 40px;display: flex;align-items: center;">
											<input type="text"value="" placeholder="____" confirm-type="done" maxlength="3" cursor-spacing="3" style="text-align: center;"/>
										</view>
										<text style="color: #FFFFFF;background-color: #00d7c3;width: 20px;font-size: 15px;">Kg</text>
									</view>
								</view>							
							</view>
							<view class="option-view">
								<text style="font-size: 20px;color: #FFFFFF;margin-top: 20px;margin-left: 20px;">值班</text>
								<view>
									<radio-group name="radio" style="line-height: 40px;width: 220px;">
										<label style="margin: 10px;">
											<radio value="radio1" /><text style="color: #FFFFFF;margin: 10rpx;">是</text>
										</label>
										<label style="margin: 10px;">
											<radio value="radio2" checked="true" /><text style="color: #FFFFFF;margin: 10rpx;">否</text>
										</label>
									</radio-group>
									<view style="display: flex;align-items: center;">
										<view class="name1-input"style="display: flex;align-items: center;margin: 10px;">
											<view style="background-color: #00d7c3;color: #FFFFFF;width: 75px;font-size: 20px;height: 40px;display: flex;align-items: center;">
												<input type="text"value="" placeholder="液体" confirm-type="done" cursor-spacing="3" style="text-align: center;"/>
											</view>
										</view>
										<view class="name2-input"style="display: flex;align-items: center;margin: 10px;">
											<view style="background-color: #00d7c3;color: #FFFFFF;width: 75px;font-size: 20px;height: 40px;display: flex;align-items: center;">
												<input type="text"value="" placeholder="成型" confirm-type="done" cursor-spacing="3" style="text-align: center;"/>
											</view>
										</view>
										<view class="name3-input"style="display: flex;align-items: center;margin: 10px;">
											<view style="background-color: #00d7c3;color: #FFFFFF;width: 75px;font-size: 20px;height: 40px;display: flex;align-items: center;">
												<input type="text"value="" placeholder="包装" confirm-type="done" cursor-spacing="3" style="text-align: center;"/>
											</view>
										</view>
									</view>
								</view>							
							</view>	
						</form>
					</view>
				</block>
			</scroll-view>
		</view>
		<button class="save">保存</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				wh:0,
				ww:0,
				active:0,
				title:'',
				arealist:[
					{area:'MD1'},
					{area:'MD2'},
					{area:'MD3'},
					{area:'MD4'},
					{area:'MD5'},
					{area:'MD6'},
					{area:'MD7'},
					{area:'Liquid'}
					
				],
				datalist:[
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''},
						{area:'',
						timeWasted:'',
						OTWasted:'',
						PWasted:''}
				]
			}
		},
		onLoad() {
			//获取设备信息
			const sysI = uni.getSystemInfoSync()
			//获取当前设备可用屏幕的高度和宽度
			this.wh=sysI.windowHeight-40
			this.ww=sysI.windowWidth-100
			console.log(this.ww)
			//绑定区域与区域数据
			for (let i = 0; i < this.arealist.length; i++) {
				this.datalist[i].area=this.arealist[i].area
			}
		},
		methods:{
			sclect(i){
				this.active=i
				this.title=this.arealist[i].area
			},
			formSubmit: function(e) {
							console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
							var formdata = e.detail.value
							uni.showModal({
								content: '表单数据内容：' + JSON.stringify(formdata),
								showCancel: false
							});
						},
						formReset: function(e) {
							console.log('清空数据')
						}
		}
	}
</script>

<style lang="scss">
page{
		background-color: #e6e6e6;
	}
	.sroll-container{
		display: flex;	
	}
	
	.moulding{
		width: 120px;
		border: solid;
		border-radius: 30px;
		border-color: #0000A0;
	}
	.moulding-view{
		align-items: center;
		border-radius: 30px;
		font-size: 25px;
		width: 100px;
		height: 120px;
		display: flex;
		flex-direction: column;
		align-items: center;
		&.active{
			background-color: #00d7c3;
		}
	}
	.save{
		background-color: #0000A0;
		font-size: 30rpx;
		color: #FFFFFF;
	}
	
</style>
