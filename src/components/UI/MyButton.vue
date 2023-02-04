<template>
	<button class="btn button">
	<slot></slot>
	</button>
</template>

<script>
export default {
	name: 'my-button',
};
</script>

<style>
/*.btn {*/
/*	cursor: pointer;*/
/*	padding: 10px 15px;*/
/*	background: none;*/
/*	color: teal;*/
/*	border: 1px solid teal;*/
/*}*/
.button {
	padding: 7px 15px;
	font-size: 16px;
	text-align: center;
	cursor: pointer;
	outline: none;
	color: #fff;
	background-color: #4CAF50;
	border: none;
	border-radius: 15px;
	box-shadow: 0 9px #999;
}

.button:hover {background-color: #3e8e41}

.button:active {
	background-color: #3e8e41;
	box-shadow: 0 5px #666;
	transform: translateY(4px);
}
</style>