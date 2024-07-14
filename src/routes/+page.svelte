<script>
	import '../reset.css';
	import Biller from './Biller.svelte';
	import Header from './Header.svelte';
	import Nav from './Nav.svelte';

	let activeMenu = false; // boolean

	function toggleMenu() {
		activeMenu = !activeMenu;
	}
</script>

<!-- *Html -->
<Header on:toggleMenu={toggleMenu} />
<Nav {activeMenu} on:toggleMenu={toggleMenu} />
<main class="center">
	<Biller />
	<aside class="center-aside">Ofertas</aside>
</main>

<style>
	:global(body) {
		display: flex;
		flex-direction: column;
	}
	.center {
		flex-grow: 1;
		display: flex;
		overflow: auto;
	}
	.center aside {
		width: 25%;
	}
</style>
