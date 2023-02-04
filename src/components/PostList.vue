<template>
	<div v-if="posts.length>0">
		
		<h3>User list:</h3>
		
		<post-item
			v-for="post in posts"
			:post="post"
			:key="post.id"
			@remove="$emit('remove', post)"
		/>
	</div>
	
	<h3 v-else style="color: red">Empty list =(</h3>
	
</template>

<script>
import PostItem from "./PostItem.vue";

export default {
	props: {
		posts: {
			type: Array,
			required: true
			
		}
	},
	components: {
		PostItem
	},
};
</script>

<style scoped>
h3 {
	margin: 10px;
}
</style>