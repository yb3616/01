<template>
	<div>
		<div> Index Page. </div>
	</div>
</template>

<script>
import axios from 'axios'
export default {
	methods: {
		getData () {
			axios.get('/test.php')
				.then(response => {
					console.log(response);
				})
				.catch(response => {
					console.log(response);
				});
		}
	},
	mounted () {
		this.getData();
	}
}
</script>

<style>
</style>
