<template>
	<section id="hero_section" class="top_cont_outer">
		<div class="hero_wrapper">
			<div class="card hovercard">
				<div class="cardheader"></div>
				<div class="avatar">
					<img alt="" :src="pf_url" />
				</div>
				<div class="info">
					<div class="title">
						<a target="_blank" href="">刘家磊</a>
					</div>
					<div class="desc"><b>{{profession}}</b></div>
					<div class="desc">
						<p>
							{{sf}}<br />
							邮箱：{{email}}<br />
							<br />
							<br /><br /><br /><br /><br /><br /><br /><br />
						</p>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
import axios from 'axios';
import pubsub from "pubsub-js"
export default {
	name: "Home",
	data(){
		return {
			profession:'',
			sf:'',
			email:'',
			pf_url:'',
		}
	},
	mounted() {
		axios.get('http://localhost:8080/static/home',).then(res=>{
			this.profession=res.data[0].profession;
			this.sf = res.data[0].sf;
			this.email = res.data[0].email;
			this.pf_url = res.data[0].pf_url;
			pubsub.publish('introduction',res.data[0].intro)
		}).catch (err=>{
			console.log(err)
		})
	},
};
</script>

<style></style>
