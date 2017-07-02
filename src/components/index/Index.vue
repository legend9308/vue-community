<template>
	<div class="index">
		<div class="header">
			<img src="static/img/vue.png" alt="">
			<span>发帖</span>
		</div>
		<div class="header-list">
			<ul>
				<li @click="read('all')"  class="active">全部</li>
				<li @click="read('good')">精华</li>
				<li @click="read('share')" >分享</li>
			</ul>
			<span class="border"></span>
		</div>
		<div class="topic">
			<div class="topic-list" v-for="topic in topicList">
			<p>{{topic.title}}</p>
		</div>
		</div>  
		<common-footer></common-footer>
	</div>


</template>




<script type="text/javascript">

	import Axios from 'axios'
	import $ from 'jquery'
	import CommonFooter from '../common/CommonFooter.vue'
	import Topic from './Topic.vue'
export default {
	data(){
		return{
			topicList:[]
		}
	},
	components:{
		CommonFooter,
		Topic
	},
	methods:{
		// change(e){
		// 	$('li').removeClass('active');
		// 	$(e.target).addClass('active');
		// 	$('.border').css('left',$('.active').index()*2.133+'rem');
		// 	console.log(111);
		// },
		read(title){
			Axios.get('https://www.vue-js.com/api/v1/topics?tab='+title)
			.then((res)=>{
				this.topicList = [];
				this.topicList = this.topicList.concat(res.data.data);
			});
			var e=event||window.event;
			$('li').removeClass('active');
			$(e.target).addClass('active');
			$('.border').css('left',$('.active').index()*2.133+'rem');
		}
	},
	mounted(){
		Axios.get('https://www.vue-js.com/api/v1/topics?tab=all')
			.then((res)=>{
				this.topicList = this.topicList.concat(res.data.data);
				console.log(this.topicList)
			});
	}
}


</script>



<style scoped type="text/css">
	@import "../../assets/css/reset.css";
	.header{
		height: 0.8rem;
		line-height: 0.8rem;
		background: #474a4f;
		position: fixed;
		width: 100%;
		top: 0;
	}
	.header img{
		width: 0.8rem;
	}
	.header span{
		float: right;
		margin-right: 0.4rem;
		color: #fff;
	}
	.header-list{
		position: fixed;
		width: 100%;
		top: 0.8rem;
		height: 0.8rem;
		line-height: 0.8rem;
		background: #474a4f;
		/*border-top: 1px solid #fff;*/
	}
	.header-list ul{
		display: flex;
		text-align: center;
	}
	.header-list li{
		flex: 1;
		color: #ccc;
	}
	.header-list .active{
		color: #fff;
	}
	.header-list .border{
		/*display: block;*/
		position: absolute;
		bottom: 0;
		left: 0;
		width: 33.3%;
		height: 2px;
		background: #f00;
		-webkit-transition: left 2s ease-in 0;
		transition: left 0.2s ease-in 0s;
	}
	.topic{
		margin-top: 1.6rem;
		margin-bottom: 1rem;
		color: #000;
		/*height: 3rem;*/
		background: #eff2f7;
	}
	.topic-list{
		background: #fff;
		margin-bottom: 0.1rem;
		/*padding: 0.4rem;*/
	}

    .loading{
     	clear: both;
    	text-align: center;
    }
</style>