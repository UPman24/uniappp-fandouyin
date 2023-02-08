<template>
	<view>
		<!-- 
		
		
		1. 引入注意点
		
		（1）common文件夹是必须的，原封不动粘贴复制即可
		
		（2）static/emojis 表情库 需要引入
		
		（3）如果使用抖音评论  static/douyin 文件需要引入
		
		（防止没有图片报错）
		
		（4）uni_modules 文件夹下的文件也需要进行拷贝
		
		（5）up 主，已经改进了 uni-popup.vue 并对此项目进行了专门的适配，所以要注意一下
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		
		 -->
		
		<view style="width: 100%; height: 120upx;"></view>
		<swiper :style="'width: '+ width +'px; height: '+ (height-60) +'px;'" indicator-dots>
			<swiper-item>
				<scroll-view style="width: 100%; height: 100%;" :scroll-y="true">
					<view style="margin-top: 30upx; margin-left: 5%; font-size: 24px; font-weight: bold;">请选择您的身份</view>
					<block v-for="(list,index) in peopleList">
						<view @click="click(index)" v-if="list.isClick" style="width: 90%; margin-left: 5%; margin-top: 30upx; border: 2px solid #7385ff; background-color: #FFFFFF; box-shadow: 1upx 1upx 18upx -10upx #7385ff; border-radius: 10upx;">
							<view style="display: flex; flex-direction: row; padding: 20upx;">
								<image mode="aspectFill" :src="list.headimage" style="width: 200upx; height: 200upx; border-radius: 20upx;"></image>
								<view style="display: flex; flex-direction: column;">
									<view style="font-size: 18px; font-weight: bold; margin-left: 30upx;">{{list.username}}</view>
									<view style="font-size: 14px; margin-left: 30upx; margin-top: 30upx;">ID：{{list._id}}</view>
								</view>
							</view>
						</view>
						<view @click="click(index)" v-if="!list.isClick" style="width: 80%; margin-left: 10%; margin-top: 30upx; background-color: #FFFFFF; box-shadow: 1upx 1upx 18upx -10upx #7385ff; border-radius: 10upx;">
							<view style="display: flex; flex-direction: row; padding: 20upx;">
								<image mode="aspectFill" :src="list.headimage" style="width: 200upx; height: 200upx; border-radius: 20upx;"></image>
								<view style="display: flex; flex-direction: column;">
									<view style="font-size: 18px; font-weight: bold; margin-left: 30upx;">{{list.username}}</view>
									<view style="font-size: 14px; margin-left: 30upx; margin-top: 30upx;">ID：{{list._id}}</view>
								</view>
							</view>
						</view>
					</block>
					<view @click="toSelectPages" style="width: 120upx; height: 120upx; margin-top: 80upx; margin-left: 42%; border-radius: 120upx; background:linear-gradient(to right,#b6c8ff,#7385ff);">
						<image src="@/static/youjiantou.png" style="width: 60upx; height: 60upx; margin-top: 30upx; margin-left: 30upx;"></image>
					</view>
					<view style="width: 100%; height: 160px;"></view>
				</scroll-view>
			</swiper-item>
			<swiper-item>
				<view @click="clearAllVideoPinlun" style="width: 90%;height: 80upx;background-color: #b6c8ff;border-radius: 80px;margin-left: 5%;">
					<view style="text-align: center;font-size: 14px;font-weight: bold;padding-top: 10px;">清除全部视频评论</view>
				</view>
				<block v-for="(list,index) in List">
					<view style="font-size: 14px;font-weight: bold;margin-top: 20px;margin-left: 20px;">{{(index+1)}}.影响了{{list}}条数据.</view>
				</block>
				<view v-if="List.length !== 0" @click="clearList" style="font-size: 14px;font-weight: bold;color: #7385ff;margin-top: 40px;margin-left: 20px;">清除以上显示</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				width: 0,
				height: 0,
				peopleList: [
					{
						headimage: "https://vkceyugu.cdn.bspapp.com/VKCEYUGU-0455454d-b373-4768-aa39-dc1226fc1362/4004e861-2246-42fd-8840-2fce3f396407.jpg",
						username: "用户一",
						_id: "abcdefghijklmn12345",
						isClick: true
					},
					{
						headimage: "https://vkceyugu.cdn.bspapp.com/VKCEYUGU-0455454d-b373-4768-aa39-dc1226fc1362/3a6ff63d-62d8-474c-90d0-9b0be85e62bb.jpg",
						username: "用户二",
						_id: "abcdefghijklmn67891",
						isClick: false
					},
					{
						headimage: "https://vkceyugu.cdn.bspapp.com/VKCEYUGU-0455454d-b373-4768-aa39-dc1226fc1362/daf9a8d5-c651-4000-8a37-7f03f70810c2.jpg",
						username: "用户三",
						_id: "abcdefghijklmn11213",
						isClick: false
					},
					{
						headimage: "https://vkceyugu.cdn.bspapp.com/VKCEYUGU-0455454d-b373-4768-aa39-dc1226fc1362/1ddb0229-36c2-41db-8f7e-c6110de13050.jpg",
						username: "用户四",
						_id: "abcdefghijklmn14151",
						isClick: false
					}
				],
				List: []
			}
		},
		onLoad() {
			this.width = uni.getSystemInfoSync().windowWidth;
			this.height = uni.getSystemInfoSync().windowHeight;
		},
		methods: {
			clearList(){
				this.List = [];
			},
			clearAllVideoPinlun(){
				uni.showLoading({
					title: 'Loging...'
				})
				uni.request({
					url: 'https://bdb24c6d-8c19-4f80-8e7e-c9c9f037f131.bspapp.com/video',
					method: 'POST',
					data:{
						info: 'get_video'
					},
					success: (res) => {
						// console.log(res);
						let data = res.data.data;
						this.List = [];
						for(let i=0;i<data.length;i++){
							new Promise((resolve,reject)=>{
								uni.request({
									url: 'https://bdb24c6d-8c19-4f80-8e7e-c9c9f037f131.bspapp.com/video',
									method: 'POST',
									data:{
										info: 'clear_pinlun',
										_id: data[i]._id
									},
									success: (re) => {
										let das = re.data.affectedDocs;
										this.List.push(das);
									}
								})
							})
						}
						uni.hideLoading();
					}
				})
			},
			click(index){
				this.peopleList[index].isClick = true
				for(let i=0;i<this.peopleList.length;i++){
					if(i !== index) {
						this.peopleList[i].isClick = false
					}
				}
			},
			toSelectPages(){
				for(let i=0;i<this.peopleList.length;i++){
					if(this.peopleList[i].isClick == true) {
						uni.setStorageSync("user",this.peopleList[i]);
					}
				}
				uni.navigateTo({
					url: '../index/index'
				})
			}
		}
	}
</script>

<style>
	
</style>
