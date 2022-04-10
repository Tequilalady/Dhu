<template>
	<view>
		<button type="primary" @click="goto('/pages/A/A')">通过方法跳转到A页面</button>
		<navigator url="../A/A"><button type="primary">A</button></navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			goto(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style lang="scss">

</style>
