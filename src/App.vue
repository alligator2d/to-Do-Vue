<template>
	
	<div class="app">
		<h1>Posts page</h1>
		<my-button @click="showDialog">Create Post</my-button>
		<my-dialog v-model:show="dialogVisible">
			<post-form
				@create="createPost"
			/>
		</my-dialog>
		
		<post-list
			:posts="posts"
			@remove="removePost"
		/>
	</div>
	
</template>

<script>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import PostItem from "./components/PostItem.vue";
import MyButton from "./components/UI/MyButton.vue";
import MyDialog from "./components/UI/MyDialog.vue";

export default {
	data() {
		return {
			posts: [
				{ id: 1, title: "JavaScript", body: "Описание поста 1" },
				{ id: 2, title: "C#", body: "Описание поста 2" },
				{ id: 3, title: "Ruby", body: "Описание поста 3" },
				{ id: 4, title: "Java", body: "Описание поста 4" }
			],
			dialogVisible: false,
		};
	},
	methods: {
		createPost(post) {
			console.log(post);
			this.posts.push(post);
			this.dialogVisible = false;
			
		},
		removePost(post) {
			this.posts = this.posts.filter(p => p.id !== post.id);
		},
		showDialog() {
			this.dialogVisible = true;
		},
	},
	components: {
		MyButton,
		MyDialog,
		PostList, PostForm, PostItem
	},
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
.app {
	padding: 20px;
}
</style>