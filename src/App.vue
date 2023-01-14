<template>
	
	<div class="app">
		
		<h1>Hello Vue3</h1>
		
		<form>
			<h4>Create post:</h4>
			<input
				v-bind:value="title"
				@input="inputTitle"
				class="input"
				type="text"
				placeholder="title...">
			<input v-bind:value="body"
				   @input="inputBody"
				   class="input"
				   type="text"
				   placeholder="body...">
			<button
				class="btn" @click="createPost">Create!
			</button>
		</form>
		<div class="post" v-for="post in posts">
			<div><strong>Название: </strong>{{ post.title }}</div>
			<div><strong>Описание: </strong>{{ post.body }}</div>
		
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			posts: [
				{ id: 1, title: "JavaScript", body: "Описание поста 1" },
				{ id: 2, title: "C#", body: "Описание поста 2" },
				{ id: 3, title: "Ruby", body: "Описание поста 3" }
			
			],
			title: "",
			body: ""
		};
	},
	methods: {
		createPost() {
			
		},
		inputTitle(event) {
			this.title = event.target.value;
		},
		inputBody(event)
		{
			this.body = event.target.value;
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

.post {
	padding: 15px;
	border: 2px solid teal;
	margin-top: 10px;
}

.input {
	width: 100%;
	border: 1px solid teal;
	padding: 15px 15px;
	margin-top: 15px;
}

.app {
	padding: 20px;
}

form {
	display: flex;
	flex-direction: column;
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
</style>