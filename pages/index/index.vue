<template>
	<view class="page">
		<!--轮播图-->
		<swiper class="carousel">
			<swiper-item v-for="item in swipers">
				<image v-bind:src="item" class="carousel"></image>
			</swiper-item>
		</swiper>
		<!--热门超英-->
		<view class="page-block super-hot">
			<view class="hot-title-warpper">
				<image src="../../static/icos/hot.png" class="hot-icon"></image>
				<view class="hot-title">
					热门超英
				</view>
			</view>
		</view>
		<!--海报-->
		<scroll-view scroll-x="true" class="page-block hot">
			<view class="single-poster" v-for="poster in posterList">
				<view class="poster-wapper">
					<image :src="poster.cover" class="poster"></image>
					<view class="movie-name">{{poster.name}}</view>
					<trailer-stars :innerScore="poster.score" showNum="1"></trailer-stars>
				</view>
			</view>
			</scroll-view>
		
	</view>
</template>

<script>
	//import common from "../../common/common.js"
	import helloComp from "../../components/helloComp.vue"
	import trailerStars from "../../components/trailerStars.vue"
	export default {
		data() {
			return {
				title: 'Hello',
				swipers:[],
				posterList:[],
				msg:"父组件传参"
			}
		},
		onLoad() {
			uni.request({
				url:this.serveUrl+"/hero/swiper",
				success:(res)=>{
					console.log(res)
					console.log(res.data);
					if(res.statusCode == 200){
						this.swipers = res.data.url;
					}else{
						console.log("error");
						console.log(res.data.status);
					}
				},
				fail:(err)=>{
					console.error(err);
				}
			});
			
			uni.request({
				url:this.serveUrl+"/hero/superhero",
				success:(res)=>{
					console.log(res)
					console.log(res.data);
					if(res.data.status == 200){
						this.posterList = res.data.data;
					}else{
						console.log("error");
						console.log(res.data.status);
					}
				},
				fail:(err)=>{
					console.error(err);
				}
			});
		},
		methods: {
			
		},
		components:{
			helloComp,trailerStars
		}
	}
</script>

<style>
	@import url("index.css");
</style>
