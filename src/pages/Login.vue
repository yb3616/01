<template>
	<div class="loginMain" ref="loginMain">
		<div class="logo">
			<h1>客户登录</h1>
		</div>
		<form @submit.prevent="submit">
			<md-input-container>
				<label>请输入帐号</label>
				<md-input placeholder="请输入帐号" autofocus required name="loginid"></md-input>
			</md-input-container>

			<md-input-container md-has-password>
				<label>请输入密码</label>
				<md-input type="password" placeholder="请输入密码" required name="password"></md-input>
			</md-input-container>

			<md-input-container md-has-password>
				<label>请重复输入密码</label>
				<md-input type="password" placeholder="请重复输入密码" required name="repasswd"></md-input>
			</md-input-container>

			<md-checkbox name="rememberme" class="md-primary">记住登录</md-checkbox>

			<md-button class="md-raised md-primary vue-submit" type="submit">登录</md-button>
		</form>
	</div>
</template>

<script>
export default {
	data () {
		return {
			headerHeight: 64
		}
	},
	mounted () {
		this.mainInit();
		window.onresize = this.mainInit;
	},
	methods: {
		mainInit () {
			let box = this.$refs.loginMain;
			let mainHeight = box.offsetHeight;
			let height = document.documentElement.clientHeight;
			let toHeight = parseFloat(
				(height - this.headerHeight*2 - mainHeight)/2
			);
			toHeight = toHeight > 0 ? toHeight : 0;
			box.style.top = toHeight + "px";
		},
		submit (e) {
			var formData = new FormData(e.target);
			console.log(formData);
		}
	}
}
</script>

<style scoped>
.loginMain {
	width: 300px;
	height: 400px;
	margin: auto;
	position: relative;
	left: 0;
}
h1 {
	margin: 0px;
}
.logo {
	width: 100%;
	height: 100px;
	line-height: 100px;
	margin: auto;
	text-align: center;
}
.vue-submit {
	float: right;
}
</style>
