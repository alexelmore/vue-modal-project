<template>
	<h1>{{ title }}</h1>
	<p>Welcome!</p>
	<teleport to=".modals" v-if="showModal">
		<Modal :theme="theme" @close="toggleModal">
			<h1 v-if="isDeal">{{ headerDeals }}</h1>
			<h2 v-if="isDeal">{{ textDeals }}</h2>
			<h1 v-if="!isDeal">{{ headerFeatures }}</h1>
			<h2 v-if="!isDeal">{{ textFeatures }}</h2>
			<template v-if="isDeal" v-slot:links>
				<div class="tags">
					<a href="#">Sign Up Now</a>
					<a href="#">More Info</a>
				</div>
			</template>
			<template v-if="!isDeal" v-slot:features>
				<div class="tags">
					<a href="#">Visit Vue</a>
					<a href="#">Read the Docs</a>
				</div>
			</template>
		</Modal>
	</teleport>
	<button class="btn" @click="toggleModal">Show Me the Deals</button>
	<button class="btn" @click="toggleFeaturesModal">
		Learn About New Features
	</button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
	name: "App",
	components: {
		Modal,
	},
	data() {
		return {
			title: "Vue All The Things!",
			headerDeals: "Sign Up NOW!",
			textDeals: "And Receive all the DEALS!",
			headerFeatures: "Vue 3 is HERE!",
			textFeatures: "Start using Vue 3 Today!",
			theme: "sale",
			showModal: false,
			isDeal: false,
		};
	},
	methods: {
		toggleModal() {
			this.showModal = !this.showModal;
			if (!this.isDeal) {
				this.isDeal = true;
			}
		},
		toggleFeaturesModal() {
			this.showModal = !this.showModal;
			if (this.isDeal) {
				this.isDeal = false;
			}
		},
	},
};
</script>

<style>
#app,
.modals {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
.btn {
	display: block;
	width: fit-content;
	font-size: 1.5em;
	color: #fff;
	padding: 8px 20px;
	border-radius: 4px;
	background-color: rgb(65, 184, 131);
	cursor: pointer;
	text-decoration: none;
	margin: 20px auto;
	border: 3px solid rgb(52, 73, 94);
}
.tags {
	display: flex;
	flex-direction: column;
}
.tags a {
	text-decoration: none;
	color: #2c3e50;
	font-size: 1em;
	font-weight: bold;
}
.tags a:hover {
	color: rgb(65, 184, 131);
}
</style>
