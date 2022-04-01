<template>
	<section id="aboutUs">
		<!--Aboutus-->
		<div class="inner_wrapper aboutUs-container fadeInLeft animated wow">
			<div class="container">
				<h2>关于我</h2>
				<div class="inner_section">
					<div class="row">
						<div class="col-lg-12 about-us">
							<div class="row">
								<div class="col-md-6">
									<h3>个人简介</h3>
									<p>
										<strong>刘家磊</strong>&emsp;&emsp;{{introduction}}
									</p>
									<h3>教育背景</h3>
									<ul class="about-us-list">
										<li class="points" v-for="(item,i) in msg" :key="i">
											{{item.msg}}
										</li>
									</ul>
								</div>
								<!-- /.col-md-6 -->
								<div class="col-md-6">
									<h3>学术兼职</h3>
									<h5 v-for="(item,i) in jobs" :key="i">{{item.job}}</h5>
								</div>
								<div class="col-md-6">
									<h3>最新动态</h3>
									<h5 v-for="(item,i) in news" :key="i">{{item.news}}</h5>
								</div>
							</div>
							<!-- /.col-md-6 -->
						</div>
						<!-- /.row -->
					</div>
					<!-- /.col-lg-12 -->
				</div>
			</div>
		</div>
	</section>
</template>

<script>
import axios from 'axios'
import pubsub from "pubsub-js"
export default {
	name: "AboutMe",
	data() {
		return {
			url:"http://localhost:8080/static",
			introduction:'',
			msg:'',
			jobs:'',
			news:''
		}
	},
	mounted() {
    this.pubId=pubsub.subscribe("introduction",(msgName,data)=> {
      this.introduction=data;
    }),
	axios.get(`${this.url}/edu`).then(res=>{
		this.msg=res.data;
	}).catch (err=>{
		console.log(err);
	})
	axios.get(`${this.url}/academic`).then(res=>{
		this.jobs=res.data;
	}).catch (err=>{
		console.log(err);
	})
	axios.get(`${this.url}/news`).then(res=>{
		this.news=res.data;
	}).catch (err=>{
		console.log(err);
	})
  },
  beforeDestroy() {
    pubsub.unsubscribe(this.pubId)
  },
};
</script>

<style></style>
