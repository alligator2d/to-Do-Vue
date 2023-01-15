<template>
	
	<div class="app">
		
		<h1>Hello Vue3</h1>
		<post-form
			@create="createPost"
		/>
		
		<post-list
			:posts="posts"
		/>
	</div>
</template>

<script>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";

export default {
	components: {
		PostList, PostForm
	},
	data() {
		return {
			posts: [
				{ id: 1, title: "JavaScript", body: "Описание поста 1" },
				{ id: 2, title: "C#", body: "Описание поста 2" },
				{ id: 3, title: "Ruby", body: "Описание поста 3" },
				{ id: 4, title: "Java", body: "Описание поста 4" }
			]
			
		};
	},
	methods: {
		createPost(post) {
			console.log(post);
			this.posts.push(post)
			
		}
		
	}
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