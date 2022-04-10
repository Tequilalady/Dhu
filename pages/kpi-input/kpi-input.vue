<template>
	<view>
		<view class="sroll-container">
			<!-- 小组选择 -->
			<scroll-view class="moulding" scroll-y="true" :style="{height: wh+'px'}" >
				<block v-for="(item,i) in arealist " :key='i'>
					<view :class="['moulding-view', active===i ? 'active' : '']" @click="sclect(i)"><text style="margin-top:40px;font-weight: bold;color: #0000A0;">{{item.area}}</text></view>
				</block>
			</scroll-view>
			<!-- 内容填写区 -->
			<scroll-view class="input" scroll-y="true" :style="{height: wh+'px'}">
				<view class="input-kpi":style="{height:wh+'px'}" style="line-height:40px;background-color: #0000A0;margin-top: 20px;margin-bottom: 20px;border-radius: 10px;">
					<view style="line-height: 40px;color: #FFFFFF;font-size: 20px;display: flex;align-items: flex-end;">
						 <text style="margin: 5px; margin-top: 20px; font-weight: bold;">季度指标</text>
						 <text style="margin: 5px; margin-top: 20px; margin-right: 30px;margin-left: 10px;font-weight: bold;" >目标值</text>
						 <text style="margin: 5px; margin-top: 20px; font-weight: bold;">达成值</text>
					</view>
					<view v-for="(item,i) in cateLv2" :key='i'>
						<view class="section" style="line-height: 60px;color: #FFFFFF;font-size: 12px;display: flex;align-items: center;">
							<text style="margin: 5px; font-weight: bold;width: 70px;text-align: center;">{{item.section}}</text>
							<view class="value-input"style="display: flex;align-items: center;margin: 10px;margin-left: 15px;">
								<view style="background-color: #00d7c3;color: #FFFFFF;width: 75px;font-size: 20px;height: 40px;display: flex;align-items: center;">
									<input type="number"value="" placeholder="____" confirm-type="done" cursor-spacing="3" style="text-align: center;"/>
								</view>
							</view>
							<view class="value-input"style="display: flex;align-items: center;margin: 10px;">
								<view style="background-color: #00d7c3;color: #FFFFFF;width: 75px;font-size: 20px;height: 40px;display: flex;align-items: center;">
									<input type="number"value="" placeholder="____" confirm-type="done" cursor-spacing="3" style="text-align: center;"/>
								</view>
							</view>
						</view>
					</view>
	</view>
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
				cateLv2:[],
				arealist:[
					{area:'安全'},
					{area:'质量'},
					{area:'精益'},
					{area:'SIG'},
					{area:'易耗'},
					{area:'Fmos'},
					{area:'超耗'}
					
				],
				datalist:[
					{area:'安全',
					goal:'',
					done:''},
					{area:'质量',
					kpiSection:[
							{section:'QualifyRisk',
							goal:'',
							done:''},
							{section:'NearMiss',
							goal:'',
							done:''},
							{section:'质量偏差',
							goal:'',
							done:''},
							{section:'精益提案',
							goal:'',
							done:''},
							{section:'质量事故',
							goal:'',
							done:''},
							{section:'QPC',
							goal:'',
							done:''},
							{section:'QIP',
							goal:'',
							done:''},
							{section:'质量评选',
							goal:'',
							done:''},
							{section:'质量投诉',
							goal:'',
							done:''}
					]
					},
					{area:'精益',
					kpiSection:[
							{section:'新增提案',
							goal:'',
							done:''},
							{section:'未过晨会',
							goal:'',
							done:''},
							{section:'已完成',
							goal:'',
							done:''}
					]},
					{area:'SIG',
					goal:'',
					done:''},
					{area:'易耗',
					goal:'',
					done:''},
					{area:'Fmos',
					goal:'',
					done:''},
					{area:'超耗',
					goal:'',
					done:''}
				]
			}
		},
		onLoad() {
			//获取设备可用窗口高度和宽度
			const sysI = uni.getSystemInfoSync()
			this.wh=sysI.windowHeight-40
			this.ww=sysI.windowWidth-120
			//初始话页面数据
			this.cateLv2=this.datalist[0].kpiSection
		},
		methods:{
			sclect(i){
				this.active=i
				this.cateLv2=this.datalist[i].kpiSection
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
