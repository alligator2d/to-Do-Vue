<template>
	<form @submit.prevent>
		<h4>Create post:</h4>
		<my-input
			v-model="post.title"
			type="text"
			placeholder="title..."
		/>
		<my-input
			v-model="post.body"
			type="text"
			placeholder="body..."
		/>
		<my-button
			style="align-self: flex-end; margin-top: 15px;"
			@click="createPost">Create!
		</my-button>
	</form>
</template>

<script>

export default {
	
	data() {
		return {
			post: {
				title: "",
				body: ""
			}
		};
	},
	methods: {
		createPost() {
			this.id = Date.now();
			this.$emit("create", this.post);
			this.post = {
				title: "",
				body: ""
			};
		}
	},
}
</script>

<style scoped>
form {
	display: flex;
	flex-direction: column;
}
</style>