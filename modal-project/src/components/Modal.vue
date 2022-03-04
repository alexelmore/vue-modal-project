<template>
	<div class="backdrop" @click.self="closeModal">
		<div class="modal" :class="{ sale: theme === 'sale' ? 'sale' : '' }">
			<slot>Default Modal Content</slot>
			<div class="actions">
				<slot name="links"></slot>
				<slot name="features"></slot>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	props: ["header", "text", "theme"],
	methods: {
		closeModal() {
			this.$emit("close");
		},
	},
};
</script>

<style>
.modal {
	width: 400px;
	padding: 20px;
	margin: 100px auto;
	background: white;
	border-radius: 10px;
}
.backdrop {
	top: 0;
	position: fixed;
	background: rgba(0, 0, 0, 0.5);
	width: 100%;
	height: 100%;
}
.modal h1 {
	color: #03cfb4;
	border: none;
	padding: 0;
}
.sale {
	background: #03cfb4;
	color: rgb(52, 73, 94);
	border: 2px solid rgb(52, 73, 94);
}

.sale h1 {
	color: rgb(52, 73, 94);
}
.sale .tags a:hover {
	color: white;
}
</style>
