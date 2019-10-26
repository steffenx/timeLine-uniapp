# 关于这个
- 这是一个简易时间轴，左中右三种位置。
- 做项目的时候看到移动官网上的一个时间轴效果，学习的写一下。
- 需要监听页面滑动加载动画。
---
属性|类型|说明|值
:---:|:--:|:---:|:---:
location|String|时间轴显示的位置|center(默认)，left，right
title|String|标题|标题
#用法
```
<template>
	<view class="content">
		<time-line ref="timeline" location="center" title="我的时间轴"></time-line>
	</view>
</template>
//引入(全局组件也可)
import timeLine from '../../components/xuan-timeLine/xuan-timeLine.vue'
components:{
  timeLine
},
onPageScroll() {
	this.$refs.timeline.getScroll();
},

//另外觉得监听太快
//也可以给监听加个定时器（都无所谓）
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
```

