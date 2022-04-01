<template>
	<section id="experience" class="timeline">
		<div class="container">
			<h2>Project</h2>
			<h6>科研项目</h6>
			<div class="qa-message-list" id="wallmessages">
				<div class="message-item" v-for="(item,p) in project" :key="p">
					<div class="message-inner">
						<div class="message-head clearfix">
							<div class="user-detail">
								<h5 class="handle">{{item.title}}</h5>
								<div class="post-meta">
									<div class="asker-meta">
										<span class="qa-message-what"></span>
										<span class="qa-message-when">
											<span class="qa-message-when-data">{{item.date}}</span>
										</span>
									</div>
								</div>
							</div>
						</div>
						<div class="qa-message-content">
							{{item.content}}
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
import axios from 'axios';
export default {
	name: "Project",
	data() {
		return {
			project:''
		}
	},
	mounted() {
		axios.get('http://localhost:8080/static/project').then(res=>{
			this.project=res.data;
		}).catch (err=>{
			console.error(err)
		})
	},
};
</script>

<style></style>
