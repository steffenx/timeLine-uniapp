<template>
	<view class="content">
		<time-line ref="timeline" location="center" title="我的时间轴"></time-line>
	</view>
</template>

<script>
	import timeLine from '../../components/xuan-timeLine/xuan-timeLine.vue'
	export default {
		components:{
			timeLine
		},
		data() {
			return {
				time:0,
				isclick:true,
			}
		},
		onPageScroll() {
			if(this.isclick){
				this.timer();
				this.$refs.timeline.getScroll();
			}
		},
		methods: {
			timer(){
				if(this.time>0){
					this.isclick=false;
					this.time--;
					setTimeout(this.timer,1)
				}
				else{
					this.isclick=true;
					this.time=10
				}
			}
		}
	}
</script>

<style>
	
</style>
