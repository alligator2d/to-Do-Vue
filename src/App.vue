<template>
	
	<div class="app">
		<header>
			<h1>Posts page</h1>
		</header>
		
		<div class="app__btns">
			
			<my-button style="margin: 10px 0"
					   @click="showDialog">
				Create Post
			</my-button>
			
			<my-button>
				<my-select v-model="selectedSort"
						   :options="sortOptions">
				</my-select>
			</my-button>
		</div>
		
		
		<my-dialog :show="dialogVisible"
				   @hide="dialogVisible=$event">
			<post-form @create="createPost"></post-form>
		</my-dialog>
		
		<post-list :posts="sortedPost"
				   @remove="removePost"
				   v-if="!isPostsLoading"
		>
		</post-list>
		<div class="loading" v-else>Loading... <img src="./assets/icons8-спиннер.gif" alt="spinner"></div>
	</div>

</template>

<script>
import axios from "axios";
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import PostItem from "./components/PostItem.vue";
import MyButton from "./components/UI/MyButton.vue";
import MyDialog from "./components/UI/MyDialog.vue";
import MySelect from "./components/UI/MySelect.vue";

export default {
	data() {
		return {
			posts: [
				// { id: 1, title: "JavaScript", body: "Описание поста 1" },
				// { id: 2, title: "C#", body: "Описание поста 2" },
				// { id: 3, title: "Ruby", body: "Описание поста 3" },
				// { id: 4, title: "Java", body: "Описание поста 4" }
			],
			dialogVisible: false,
			isPostsLoading: false,
			selectedSort: "",
			sortOptions: [
				{ value: "title", name: "По названию" },
				{ value: "body", name: "По содержанию" }
			]
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
		async fetchPosts() {
			try {
				this.isPostsLoading = true;
				setTimeout(async () => {
					const res = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10");
					this.posts = res.data;
					this.isPostsLoading = false;
					
				}, 1000);
				
			} catch (e) {
				console.log("error");
			}
		}
	},
	watch: {
		// selectedSort(newValue){
		// 	this.posts.sort((post1, post2) => {
		// 		return post1[newValue]?.localeCompare(post2[newValue])
		// 	})
		// },
	},
	computed: {
		sortedPost() {
			return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]));
		}
	},
	mounted() {
		this.fetchPosts();
	},
	components: {
		MySelect,
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
	/*background-color: #dddee1;*/
}

.app {
	padding: 20px;
}

header {
	height: 70px;
	margin: 10px 0 50px;
	text-align: center;
}

.loading {
	margin: 20px;
}

.app__btns {
	display: flex;
	justify-content: space-between;
}
</style>