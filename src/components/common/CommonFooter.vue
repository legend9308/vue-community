<template>
	<div class="footer">
		<ul>
			<li><router-link to="/movie">首页</router-link></li>
			<li><router-link to="/music">信息</router-link></li>
			<li><router-link to="/book">我的</router-link></li>
			<li><router-link to="/photo">更多</router-link></li>
		</ul>
	</div>	
</template>



<script>
export default {
  data () {
    return {
    }
  },
  methods:{
  	
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.footer{
			height: 1rem;
			/*background: rgb(33,150,243);*/
			background: #474a4f;
	}
	.footer ul{
		display: flex;
	}
    .footer ul li{
		flex: 1;
		text-align: center;
		height: 1rem;
		line-height: 1rem;
		/*font-size: 14px;*/
	}
	.footer{
			position: fixed;
			bottom: 0;
			width: 100%;
		}
	.footer a{
	  color: #7e848c;
	  outline: none;
	}
	.footer a.router-link-active{
	  color: #fff;
	}
</style>
