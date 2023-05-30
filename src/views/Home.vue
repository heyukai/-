<template>
	<div>
		<div class="header">
			<div class="section_inner">
				<div class="section_inner_wrap">
					<h1 class="market_title">
						BUAA书城
					</h1>
					<div class="section_inner_right">
						<ul class="ul_top">
							<li class="li_nav_top">
								<router-link to="/home" class="top_nav_link">首页</router-link>
							</li>
							<li class="li_nav_top">
								<router-link to="/guanli" class="top_nav_link">管理页面</router-link>
							</li>
							<li class="li_nav_top">
								<router-link to="/readbook" class="top_nav_link">阅读页面</router-link>
							</li>
							<li class="li_nav_top">
								<router-link to="/library" class="top_nav_link">进入书城</router-link>
							</li>
						</ul>
						<div class="book_search">
							<input type="text" v-model="booksearch" id="booksearch" name="booksearch"
								placeholder="请输入书名" autocomplete="off">
							<i class="el-icon-search" @click="search()"></i>
						</div>
						<div>
						</div>
					</div>
					<div style="cursor: pointer;">

					</div>
				</div>
			</div>
		</div>
		<div style="float: right;margin-top: -68px;margin-right: 40px;line-height: 60px;">
			<div @click="selfmessage()" style="display: block;float: left;">
				<img class="avatar" style="margin-top: 10px;margin-right: 5px; float: left;"
					src="../assets/yomu.jpg" alt="">
				<div style="color:blue;float: left;margin-left: 5px;">
					{{this.isName}}
				</div>
			</div>
			<a @click="exit()" style="margin-left: 18px; margin-top: 18px; cursor:pointer;color: #9e9e9e;">退出</a>
		</div>
		<div class="container">
			<router-view v-on:loginstate="loginstate"></router-view>
		</div>
	</div>
    <div class="welcome">
        <h1>
            欢迎来到BUAA书城
        </h1>
        <h1>
            根据您的兴趣,我们为您推荐了如下书籍
        </h1>
    </div>
    <div class="book">

    </div>
</template>

<script>
	export default {
        name: "homePage",
		created() {
			var userJsonStr = sessionStorage.getItem('userData');
            var userdata = JSON.parse(userJsonStr);
            this.isName = userdata.username;
		},
		data() {
			return {
				booksearch: '',
				isName: false,
			}
		},
		components: {
			
		},
		methods: {
			search() {
				
			},
			clikelogin() {
				this.$router.push('/login')
			},
			clikeregister() {
				this.$router.push('/register')
			},
			exit() {
                sessionStorage.removeItem("userData")
				this.$router.push('/login')
			},
            selfmessage() {
				this.$router.push('/self')
			},
		}
	}
</script>

<style scoped>
	*,
	body,
	ul,
	li,
	h1,
	h2,
	h3,
	h4,
	h5 {
		margin: 0;
		padding: 0;
	}

	a {
		text-decoration: none;
		outline: none;
		color: #9e9e9e;
		font-family: "Microsoft Yahei", arial, sans-serif;
	}

	i {
		font-style: normal;
		font-weight: normal;
	}

	body {
		color: #9e9e9e;
		font: 12px/20px "Microsoft Yahei", arial, sans-serif;
		background: #f0f0f0;
		font-weight: normal;
		max-width: 100%;
		min-width: 100%;
	}

	ul,
	li {
		overflow: hidden;
	}

	.header {
		width: 100%;
		height: 68px;
		min-width: 100%;
		/* position: fixed; */
	}

	.section_inner {
		/* width: 1903px; */
		height: 68px;
		background-color: #fff;
	}

	.section_inner_wrap {
		width: 1100px;
		height: 68px;
		line-height: 68px;
		margin: 0 auto;
		padding: 0 2px;
	}

	.section_inner_wrap h1 {
		float: left;
		height: 68px;
		font-style: normal;
		font-weight: normal;
	}

	.market_title {
		font-size: 24px;
	}

	.section_inner_right {
		float: right;
		height: 68px;
	}

	.ul_top {
		float: left;
		overflow: hidden;
	}

	.li_nav_top {
		position: relative;
		float: left;
		margin-left: 20px;
		list-style: none;
		border-bottom: 3px solid transparent;
		height: 50px;
		color: #9e9e9e;
		transition: 0.5s;
	}

	.li_nav_top:hover {
		border-bottom-color: #FF5858;
		color: #000;
	}

	.top_nav_link {
		display: block;
		padding: 0 20px;
		text-align: center;
		font-size: 18px;
	}

	.book_search {
		float: left;
		position: relative;
		/* margin-left: 300px; */
	}

	.book_search input {
		width: 200px;
		height: 30px;
		line-height: 30px;
		border: 1px solid #d2d2d2;
		border-radius: 50px;
		color: #9e9e9e;
		margin: 0 22px 0 20px;
		padding: 0 36px 0 12px;
		font-size: 15px;
		outline: none;
		background: none;
	}

	.book_search input:hover {
		border-color: chocolate;
	}

	.el-icon-search {
		width: 15px;
		height: 15px;
		cursor: pointer;
		position: absolute;
		right: 40px;
		top: 27px;
	}

	.login_register {
		float: left;
		position: relative;
	}

	.el-icon-user {
		margin-left: 15px;
		margin-right: 5px;
	}

	.login_register a:hover {
		color: #f60;
		transition: 0.3s;
	}

	.container {
		width: 100%;
		/* padding-top: 68px; */
	}

	.avatar {
		width: 40px;
		height: 40px;
		border-radius: 40px;
	}

	.regist-btn {
		margin-top: -59px;
		margin-left: 60px;
	}
    .welcome{
        margin-top: 50px;
        text-align: center;
        width: 100%;
        height: 500px;
    }
</style>
