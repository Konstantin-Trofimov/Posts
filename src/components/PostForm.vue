<template>
	<form @submit.prevent="submit">
		<input 
		type="text" 
		placeholder="title"
		v-model="title">
		<input 
		type="text" 
		placeholder="body"
		v-model="body">
		<button type="submit">Create Post</button>
	</form>
</template>

<script>
	import {mapMutations} from 'vuex'
	export default {
		data() {
			return {
				title: '',
				body: ''
			};
		},
		methods: {
			...mapMutations(['createPost']),
			submit() {
				this.createPost({
					title: this.title,
					body: this.body,
					id: Date.now()
				})

				this.title = this.body = '';
			}
		}
	}
</script>

<style scoped>
	input {
		display: block;
		width: 100%;
		border: 1px solid #ccc;
		padding: 10px;
		margin-bottom: 10px; 
	}

	button {
		border-radius: .3rem;
		border: none;
		height: 2rem;
		width: 7rem;
		background: rgb(42, 96, 194);
		font-weight: bold;
		color: #ffff;
		font-size: 16px;
		cursor: pointer;
		transition: .8s;
	}

	button:focus, input:focus {
		outline: none;
	}

	button:hover {
		background: linear-gradient(217deg, rgba(255,0,0,.8), rgba(255,0,0,0) 70.71%),
            linear-gradient(127deg, rgba(0,255,0,.8), rgba(0,255,0,0) 70.71%),
            linear-gradient(336deg, rgba(0,0,255,.8), rgba(0,0,255,0) 70.71%);
		
	}
	

</style>