<template>
	<form @submit.prevent>
		<h4>Create post:</h4>
		<input
			v-model="post.title"
			class="input"
			type="text"
			placeholder="title...">
		<input
			v-model="post.body"
			class="input"
			type="text"
			placeholder="body...">
		<button
			class="btn"
			@click="createPost">Create!
		</button>
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
			// const newPost = {
			// 	id: Date.now(),
			// 	title: this.title,
			// 	body: this.body
			// };
			this.id = Date.now();
			// this.posts.push(newPost);
			this.$emit('create', this.post)
			this.post = {
				title: "",
				body: "",
			}
			this.title = "";
			this.body = "";
		}
	}
};
</script>

<style scoped>
.input {
	width: 100%;
	border: 1px solid teal;
	padding: 15px 15px;
	margin-top: 15px;
}

.btn {
	margin-top: 15px;
	cursor: pointer;
	align-self: flex-end;
	padding: 10px 15px;
	background: none;
	color: teal;
	border: 1px solid teal;

}

form {
	display: flex;
	flex-direction: column;
}
</style>