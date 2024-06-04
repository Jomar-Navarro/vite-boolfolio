<script>
import axios from "axios";
import { store } from "../data/store";
export default {
	name: "projects",

	data() {
		return {
			projects: [],
			loading: true,
			error: false,
		};
	},

	methods: {
		getApi() {
			axios
				.get(store.apiUrl)
				.then((result) => {
					this.loading = false;
					this.projects = result.data;
					console.log(this.projects);
				})
				.catch((error) => {
					this.loading = false;
					console.log(error);
					this.error = error.message;
				});
		},
	},

	mounted() {
		this.getApi();
	},
};
</script>

<template>
	<div>
		<div class="main-wrapper">
			<div class="container my-5">
				<h1>Boolfolio Home</h1>
				<div v-if="!loading">
					<h3>My Projects</h3>

					<div class="d-flex">
						<div
							v-for="project in projects"
							:key="project.id"
							class="card mx-2"
							style="width: 18rem"
						>
							<img
								:src="project.image"
								class="card-img-top"
								:alt="projects.title"
							/>
							<div class="card-body">
								<h5 class="card-title">{{ project.title }}</h5>
								<p class="card-text">{{ project.description }}</p>
								<router-link
									:to="{ name: 'details', params: { slug: project.slug } }"
									class="btn btn-info"
									>Show Details</router-link
								>
							</div>
						</div>
					</div>
				</div>
				<p v-else>loading...</p>
			</div>
		</div>
	</div>
</template>

<style lang="scss" scoped></style>
