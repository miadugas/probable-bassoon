<template>
	<Navbar />
	<div>
		<WebViewer
			initialDoc="https://pdftron.s3.amazonaws.com/downloads/pl/demo-annotated.pdf" />
	</div>
</template>

<script lang="ts">
	import Navbar from './components/Navbar.vue';
	import WebViewer from './components/WebViewer.vue';

	export default {
		name: 'App',
		components: {
			WebViewer,
			Navbar,
		},
	};
</script>

<style scoped></style>
