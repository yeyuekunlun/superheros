<template name="helloComp">
	<view>
		{{msg}}
		<view>
<!-- 			<input :value="myVal" type="text" class="txt"/>
 -->			
			<span>{{myVal}}</span>
		</view>
	</view>
	
</template>

<script>
	export default {
		name:"helloComp",
		data() {
			return {
				msg:"hello vue~~~"
			};
		},
		props:{
			myVal:{
				type:String
			}
		}
	}
	
</script>

<style>
.txt{
	color: #007AFF;
}
</style>
