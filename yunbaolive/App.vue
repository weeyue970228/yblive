<script>
	
	export default {
		globalData: {
			userinfo:[],
			site_url:'http://live2.yyyybbbb.com',
			socket_url: "ws://live2.yyyybbbb.com:19999",
		},  
		onLaunch: function() { 
			//是否登录判断
			global.isLogin = function(){
				var uid  = uni.getStorageSync('uid');
				var token  = uni.getStorageSync('token');
				if(uid == '' || token == ''){
				 	return false;
				}else{
					//判断token是否有效
					uni.request({
						url: '/appapi/?service=User.iftoken',
						method: 'GET',
						data: {
							uid:uid,
							token:token,
						},
						success: res => {
							var data=res.data.data;
							if(data['code']!=0){
								uni.showModal({
									title:'请登录',
									content:data['msg'],
									success:function(){
										uni.navigateTo({
											url:'../login/login'
										});
									}
								});
								uni.removeStorageSync('uid');
								uni.removeStorageSync('token');
								return false;
							}						
						},
					});
					
				 	return [uid,token];
				}
			};
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import './common/uni.css';
</style>
