<template>
	
	<div class="app">
		<header>
			<h1>Posts page</h1>
		</header>
		
		<my-button style="margin: 10px"
				   @click="fetchUsers">
			Get Posts
		</my-button>
		
		<my-button style="margin: 10px 0"
				   @click="showDialog">
			Create Post
		</my-button>
		
		<my-dialog :show="dialogVisible"
				   @hide="dialogVisible=$event">
			<post-form @create="createPost"></post-form>
		</my-dialog>
		
		<post-list :posts="posts"
				   @remove="removePost">
		</post-list>
	</div>

</template>

<script>
import axios from "axios";
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
			dialogVisible: false
		};
	},
	methods: {
		createPost(post) {
			this.posts.push(post);
			this.dialogVisible = false;
			
		},
		removePost(post) {
			this.posts = this.posts.filter(p => p.id !== post.id);
		},
		showDialog() {
			this.dialogVisible = true;
		},
		async fetchUsers() {
			try {
				const res = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10");
				this.posts = await res.data;
				console.log(this.posts);
			} catch (e) {
				console.log("error");
			}
		}
		// changeDialogVisible(value) {
		// 	this.dialogVisible = value;
		// }
	},
	components: {
		MyButton,
		MyDialog,
		PostList, PostForm, PostItem
	}
};
</script>

<style>
* {
	font-family: 'Montserrat', sans-serif;
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	background-color: #dddee1;
}

.app {
	padding: 20px;
}

header {
	height: 70px;
	margin: 10px 0 50px;
	text-align: center;
	/*background-color: #4CAF50;*/
}
</style>