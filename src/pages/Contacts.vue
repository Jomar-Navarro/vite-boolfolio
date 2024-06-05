<script>
import axios from "axios";
import { store } from "@/data/store";
import Loader from "../components/partials/Loader.vue";
export default {
	name: "contacts",

	components: {
		Loader,
	},

	data() {
		return {
			name: "Ken",
			email: "Okazashi@ken.it",
			message: "",
			sending: false,
			sent: false,
			error: null,
			errors: {
				name: "",
				email: "",
				message: "",
			},
		};
	},

	methods: {
		sendEmail() {
			this.sending = true;
			this.error = null;

			const data = {
				name: this.name,
				email: this.email,
				message: this.message,
			};

			axios
				.post(store.apiUrl + "send-email/", data)
				.then((result) => {
					this.sending = false;
					if (result.data.success) {
						this.sent = true;
					} else {
						this.error = "Failed to send the email. Please try again.";
					}
				})
				.catch((err) => {
					this.sending = false;
					this.error = "An error occurred: " + err.message;
				});
		},
	},
};
</script>

<template>
	<div id="contacts" class="container w-75 p-5">
		<h1>Contacts</h1>
		<div v-if="error" class="alert alert-danger">{{ error }}</div>
		<div v-if="!sending">
			<form v-if="!sent" @submit.prevent="sendEmail">
				<div class="mb-3">
					<label for="name" class="form-label">Name</label>
					<input
						v-model="name"
						type="text"
						name="name"
						class="form-control"
						id="name"
						placeholder="Name"
					/>
				</div>
				<div class="mb-3">
					<label for="email" class="form-label">Email address</label>
					<input
						v-model="email"
						type="email"
						name="email"
						class="form-control"
						id="email"
						placeholder="name@example.com"
					/>
				</div>
				<div class="mb-3">
					<label for="message" class="form-label">Message</label>
					<textarea
						v-model="message"
						name="message"
						class="form-control"
						id="message"
						rows="3"
					></textarea>
					<div class="mt-3">
						<button type="submit" class="btn btn-success">Submit</button>
					</div>
				</div>
			</form>
			<h3 v-else>Email sent successfully!</h3>
		</div>
		<Loader v-else />
	</div>
</template>

<style lang="scss" scoped>
#contacts {
	border: 1px solid white;
	border-radius: 30px;
}
</style>
