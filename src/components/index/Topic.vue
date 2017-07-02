<template>
	<div class="topic">
		<div class="topic-list" v-for="topic in topicList">
			<p>{{topic.title}}</p>
		</div>
	</div>

</template>




<script type="text/javascript">
	
	import Axios from 'axios'
	
export default {
	data(){
		return{
			topicList:[]
		}
	},
	components:{
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