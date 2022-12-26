<template>
	<view style="background-color: #000000;">
		<scroll-view :style="'width: 100%; height: '+ (windowHeight) +'px; background-color: #000000;'" :scroll-y="true" @scrolltolower="scrolltolower" :lower-threshold="lowerThreshold">
			<view style="display: flex; flex-direction: row; flex-wrap: wrap;">
				<block v-for="(list,index) in dataList" :key="index">
					<view style="width: 32.5%; height: 350upx; background-color: #000000; margin-top: 5upx; margin-left: 5upx;">
						<image @click="towxh5Video(index)" :src="list.src+'?x-oss-process=video/snapshot,t_1000,f_jpg'" mode="aspectFill" style="width: 100%; height: 100%;"></image>
					</view>
				</block>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				windowWidth: 0,
				windowHeight: 0,
				dataList: [],
				lowerThreshold: 0,
				page: 1
			}
		},
		onLoad() {
			this.windowWidth = uni.getSystemInfoSync().windowWidth
			if(uni.getSystemInfoSync().platform == 'ios'){
				var model = uni.getSystemInfoSync().model
				if(model !== 'iPhone6' || model !== 'iPhone6s' || model !== 'iPhone7' || model !== 'iPhone8'){
					this.windowHeight = (uni.getSystemInfoSync().screenHeight)-125
				} else {
					this.windowHeight = uni.getSystemInfoSync().screenHeight
				}
			} else {
				this.windowHeight = uni.getSystemInfoSync().screenHeight
			}
			this.get()
		},
		methods: {
			towxh5Video(index){
				let list = []
				let videoNumber = 36;//（请输入 6 的倍数，来控制 DOM 节点的总视频数量）
				let dotNumber = videoNumber/2;
				let inf = (index+1) - dotNumber;
				console.log('点击了第'+(index+1)+'个视频.');
				let beforeLocation = 0;
				let afterLocation = 0;
				let location = 0;
				if(inf <= 0){
					beforeLocation = 0;
					location = index;
					for(let i=0;i<=index;i++){
						list.push(this.dataList[i]);
					}
				} else {
					beforeLocation = inf;
					location = index - inf;
					for(let i=inf;i<=index;i++){
						list.push(this.dataList[i]);
					}
				}
				let onf = this.dataList.length - (index+1)
				console.log('下方视频数：'+onf);
				if(onf <= dotNumber){
					if(onf !== 0){
						afterLocation = this.dataList.length - 1;
						for(let i=index+1;i<this.dataList.length;i++){
							list.push(this.dataList[i]);
						}
					} else {
						afterLocation = this.dataList.length - 1;
					}
				} else {
					afterLocation = index+dotNumber;
					for(let i=index+1;i<=index+dotNumber;i++){
						list.push(this.dataList[i]);
					}
				}
				console.log('总视频数：'+list.length);
				console.log('\n\n第一个视频下标：'+beforeLocation+'.\n'+'最后一个视频下标：'+afterLocation+'.\n\n');
				uni.setStorageSync("List",this.dataList);
				uni.setStorageSync("dataList",list);
				uni.navigateTo({
					url: './wxh5infoVideo/wxh5infoVideo?option='+location+'&page='+this.page+'&index='+index,
				})
			},
			scrolltolower(){
				// 这里就是数据加载完以后再向后端发送数据的地方
				this.page++;
				uni.request({
					url: 'https://bdb24c6d-8c19-4f80-8e7e-c9c9f037f131.bspapp.com/video',
					method: 'POST',
					data:{
						info: 'get_video'
					},
					success: (res) => {
						var msg = res.data.data
						for (let i = 0; i < msg.length; i++) {
							this.dataList.push(msg[i])
						}
					}
				})
			},
			get(){
				uni.request({
					url: 'https://bdb24c6d-8c19-4f80-8e7e-c9c9f037f131.bspapp.com/video',
					method: 'POST',
					data:{
						info: 'get_video'
					},
					success: (res) => {
						var msg = res.data.data
						// console.log(msg)
						this.dataList = msg
					}
				})
			}
		}
	}
</script>

<style>

</style>
