<template>
	<view class="content">
		<view @tap="playVideo">全屏播放(可修改为电商商品视频点击)</view>
		<video id="myvideo" @fullscreenchange="videoControl" :src="videosrc"></video>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				videoContext:null,
				videosrc:'http://tbm-auth.alicdn.com/e99361edd833010b/GHtMSWcmEesL8KSLPqY/Jn6392sS6JSP7U7CukL_253205498109_hd_hq.mp4?auth_key=1584643579-0-0-49dc665957c68f711434fd5fc8b2e71d'
			}
		},
		onLoad() {
      
		},
		methods: {
			playVideo(){
				console.log('点击全屏,我要全屏了')
				// 全屏
				this.$nextTick(()=>{
					// requestFullScreen全屏 direction 屏幕得角度！
					this.videoContext.requestFullScreen({
						direction:0
					})
				})
			},
			videoControl(e){
				console.log(e)
				if(e.detail.fullScreen){  //e.detail.fullScreen是否为全屏
					this.videoContext.play();
				}else{
					//停止播放
					// this.videoContext.stop();   各位老板不要选择stop 选择了stop 缩小视频还会自动播放
					this.videoContext.pause();
				}
			}
		},
		onReady(){
			// 页面初次渲染！  createVideoContext uni video自带 上下文 如果不懂可以去百度
			this.videoContext = uni.createVideoContext('myvideo');
		}
	}
</script>

<style>

</style>
