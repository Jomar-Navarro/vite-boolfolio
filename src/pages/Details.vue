<script>
import axios from "axios";
import { store } from "@/data/store";
export default {
	name: "Details",

	data() {
		return {
			project: {},
		};
	},

	methods: {
		getApi() {
			const slug = this.$route.params.slug;
			axios
				.get(store + "project-by-slug/" + slug)
				.then((result) => {
					this.project = result.data.project;
					console.log(this.project);
				})
				.catch((error) => {
					console.log(error.message);
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
		<h1>~ {{ project.title }} ~</h1>
		<p>
			{{ project.description }}
		</p>
	</div>
</template>

<style lang="scss" scoped></style>
