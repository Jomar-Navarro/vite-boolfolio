<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
	components: {
		Header,
		Main,
	},
};
</script>

<template>
	<Header />
	<Main />
	<div class="container my-5">
		<router-view></router-view>
	</div>
</template>

<style lang="scss" scoped></style>
