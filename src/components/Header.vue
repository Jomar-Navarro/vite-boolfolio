<script>
export default {
	name: "Header",
};
</script>

<template>
	<header class="d-flex align-items-center">
		<div class="container">
			<nav class="navbar navbar-expand-lg" data-bs-theme="dark">
				<div class="container-fluid">
					<a class="navbar-brand fw-bolder fs-3" href="#">Boolfolio</a>
					<button
						class="navbar-toggler"
						type="button"
						data-bs-toggle="collapse"
						data-bs-target="#navbarSupportedContent"
						aria-controls="navbarSupportedContent"
						aria-expanded="false"
						aria-label="Toggle navigation"
					>
						<span class="navbar-toggler-icon"></span>
					</button>
					<div class="collapse navbar-collapse" id="navbarSupportedContent">
						<ul class="navbar-nav me-auto mb-2 mb-lg-0">
							<li class="nav-item">
								<router-link class="nav-link" :to="{ name: 'home' }"
									>Home</router-link
								>
							</li>
							<li class="nav-item">
								<router-link class="nav-link" :to="{ name: 'projects' }"
									>My Projects</router-link
								>
							</li>
							<li class="nav-item">
								<router-link class="nav-link" :to="{ name: 'about' }"
									>About</router-link
								>
							</li>
							<li class="nav-item">
								<router-link class="nav-link" :to="{ name: 'contacts' }"
									>Contacts</router-link
								>
							</li>
						</ul>
						<form class="d-flex" role="search">
							<input
								class="form-control me-2"
								type="search"
								placeholder="Search"
								aria-label="Search"
							/>
							<button class="btn btn-outline-success" type="submit">
								Search
							</button>
						</form>
					</div>
				</div>
			</nav>
		</div>
	</header>
</template>

<style lang="scss" scoped></style>
