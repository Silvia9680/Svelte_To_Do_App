<script>
	import Navbar from './components/Navbar.svelte';
	import Task from './components/Task.svelte';
</script>

<main class="fondo">
	<Navbar />
	<Task />
</main>

<style>
	.fondo {
		background-image: url(../assets/img/img1.jpg);
		height: 100vh;
		background-position: center;
		background-size: cover;
	}
</style>