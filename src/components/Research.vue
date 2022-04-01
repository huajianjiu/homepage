<template>
	<section id="Portfolio" class="content">
		<!-- Container -->
		<div class="container portfolio_title">
			<!-- Title -->
			<div class="section-title">
				<h2>Research</h2>
				<h6>主要研究方向及课题</h6>
			</div>
			<!--/Title -->
		</div>
		<div class="portfolio">
			<div id="filters" class="sixteen columns">
				<ul class="clearfix">
					<li>
						<a id="all" href="#" data-filter="*" class="active">
							<!-- <h5>All</h5> -->
						</a>
					</li>
				</ul>
			</div>
			<!--/Portfolio Filters -->

			<!-- Portfolio Wrapper -->
			<div
				class="isotope fadeInLeft animated wow grid"
				style="
					position: relative;
					overflow: hidden;
					height: 480px;
					text-align: center;
				"
				id="portfolio_wrapper"
			>
				<!-- Portfolio Item-->
				<template v-if="research.length > 0">
					<template v-for="(item, index) in research">
						<figure
							:key="index"
							style="
								position: absolute;
								left: 0px;
								top: 0px;
								transform: translate3d(337px, 0px, 0px) scale3d(1, 1, 1);
								width: 337px;
								opacity: 1;
							"
							class="portfolio-item one-four design isotope-item effect-oscar"
						>
							<div class="portfolio_img">
								<img src="images/research1.jpg" alt="Portfolio 1" />
							</div>
							<figcaption>
								<div>
									<a :href="item.detail_url" class="fancybox">
										<h2>方向一</h2>
										<p>{{ item.title }}</p>
									</a>
								</div>
							</figcaption>
						</figure>
						<div :key="index+1000" class="portfolio-item one-four">
							<h4 class="prjt">方向介绍：</h4>
							<p class="prjt prjts">
								{{ item.detail }}
								<br />
								<strong>具体技术：</strong>{{ item.technology }}
								<br />
								<strong>应用领域：</strong>
								{{ item.area }}
							</p>
						</div>
					</template>
				</template>
			</div>
			<!--/Portfolio Wrapper -->
		</div>
		<!--/Portfolio Filters -->

		<div class="portfolio_btm"></div>

		<div id="project_container">
			<div class="clear"></div>
			<div id="project_data"></div>
		</div>
	</section>
</template>

<script>
import axios from "axios";
export default {
	name: "Research",
	data() {
		return {
			research: [],
		};
	},
	beforeCreate() {
		// console
		axios
			.get("/static/research")
			.then(response => {
				this.research = response.data;
				console.log(this.research);
			})
			.catch(error => {
				console.log(error);
			});
	},
	// },
	// methods: {
	// 	getResearch() {
	// 		axios
	// 			.get("/static/research")
	// 			.then(({ data }) => {
	// 				setTimeout(() => {
	// 					this.research = data;
	// 				}, 100);
	// 				console.log(this.research);

	// 			})
	// 			.catch(err => {
	// 				console.log(err);
	// 			});
	// 	},
	// },
	// mounted() {
	// 	this.getResearch();
	// },
};
</script>

<style></style>
