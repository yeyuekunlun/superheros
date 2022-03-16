<template>
	<view name="trailerStars">
		<view class="movie-score-wapper">
			<image src="../static/icos/star-yellow.png" class="star-ico" v-for="star in yellowStar"></image>
			<image src="../static/icos/star-gray.png" class="star-ico" v-for="star in greyStar"></image>
			<view class="movie-score" v-if="showNum==1">{{innerScore}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"trailerStars",
		data() {
			return {
				yellowStar:0,
				greyStar:5
			};
		},
		props:{
			showNum:{
				type:Number,
				default:0
			},
			innerScore:0
		},
		created() {
			// var tempScore = 0;
			if(this.innerScore!=null&&this.innerScore!=undefined&&this.innerScore!=''){
				//tempScore = this.innerScore;
				this.yellowStar = parseInt(this.innerScore/2);
				this.greyStar = 5 - this.yellowStar;
			}
			// var yellowScore = parseInt(tempScore/2);
			// var greyScore = 5-yellowScore;
			// this.yellowStar = yellowScore;
			// this.greyStar = greyScore;
		}
	}
</script>

<style>
.movie-score-wapper {
	display: flex;
	flex-direction: row;
}
	
.star-ico {
	width: 20upx;
	height: 20upx;
	margin-top: 6upx;
}
.movie-score {
	font-size: 12px;
	color: grey;
	margin-left: 8upx;
}
</style>
