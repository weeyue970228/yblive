<template>
	<!-- 礼物列表 -->
	<view class="gift_list" v-show="!gift_flag">
		<view class="tit">礼物</view>
		<view class="gift_ul">
			<view class="lils">
				<image src="../../../static/live/gift_33.png" mode="" class="gift_icon"></image>
				<view class="gift_name"><text class="g_n_t">甜甜圈</text></view>
				<view class="gift_coin"><text class="g_c_t">10钻石</text></view>
			</view>
		</view>
		<view class="operate">
			<view class="balance">
				<image src="../../../static/live/drill.png" class="drill"></image>
				<text class="quota">{{coin}}</text>
				<text class="charge">充值</text>
				<uni-icons type="forward" class="forward"></uni-icons>
			</view>
			<view class="give" @click="gift_give"><text class="give_t" @click="open(['slide-left'])">赠送</text></view>
		</view>
		
	</view>
</template>

<script>
	export default {
		name:"live-gift",
		props:{
			gift_flag:{
				type:Boolean,
				default:""
			},
			coin:{
				type:String,
				default:"0"
			},
		},
		methods:{
			open(e) {
				this.$emit('open',e)
			},
			gift_give(){
				this.$emit('gift_give')
			}
		}
	}
</script>

<style>
	/* 礼物列表 */
	.gift_list{
		width: 100%;
		height: 280px;
		background-color: #000;
		position: absolute;
		bottom: 0px;
	}
	.gift_list .tit{
		width: 40px;
		height: 40px;
		line-height: 40px;
		font-size: 16px;
		color: #fff;
		text-align: center;
		border-bottom: 2px solid #fff;
		margin-left: 10px;
	}
	.gift_list .gift_ul{
		margin-top: 20px;
		width: 98%;
		height: 160px;
		margin-left: 1%;
	}
	.gift_list .lils{
		width: 115px;
		height: 110px;
		padding-top: 10px;
		text-align: center;
		border: 1px solid #FFFFFF;
	}
	.gift_list .lils .gift_icon{
		width: 40px;
		height: 40px;
	}
	.gift_list .lils .gift_name{
		
		height: 20px;
		line-height: 20px;
	}
	.gift_list .lils .gift_name .g_n_t{
		font-size: 16px;
		color: #fff;
		
	}
	.gift_list .lils .gift_coin{
		
		height: 20px;
		line-height: 20px;
	}
	.gift_list .lils .gift_coin .g_c_t{
		font-size: 13px;
		color: #CCCCCC;
		
	}
	
	.operate{
		width: 98vw;
		padding: 0 1vw;
		height: 60px;
		line-height: 60px;
		position: relative;
	}
	.operate .balance .drill{
		width: 35px;
		height: 35px;
		top:8px;
	}
	.operate .balance .quota{
		font-size: 18px;
		color: #FFFFFF;
		margin-left: 6px;
	}
	.operate .balance .charge{
		font-size: 19px;
		color: #007aff;
		margin-left: 8px;
	}
	.operate .balance .forward{
		color: #FFFFFF !important;
		font-size: 18px !important;
	}
	.operate .give{
		width: 80px;
		height: 35px;
		background-color: #F36435;
		position: absolute;
		top: 10px;
		top: 13px;
		right: 1.5%;
		line-height: 30px;
		text-align: center;
		border-radius: 20px;
	}
	.operate .give .give_t{
		font-size: 16px;
		color: #FFFFFF;
	}
</style>
