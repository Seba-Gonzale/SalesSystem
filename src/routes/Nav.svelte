<script>
	import { onMount } from 'svelte';
	import { fade, fly, blur, slide, scale, draw, crossfade } from 'svelte/transition';
	import { createEventDispatcher } from 'svelte';

	export let activeMenu;
	let dispatch = createEventDispatcher();

	function toggleMenu() {
		dispatch('toggleMenu');
	}
</script>

{#if activeMenu}
	<nav class="nav" transition:slide={{ axis: 'x' }} on:mouseleave={activeMenu ? toggleMenu : null}>
		<button class="back-button" on:click={toggleMenu}
			><img src="atras.png" alt="atrás" class="icon" /></button
		>
		<ul class="menu">
			<li>
				<a href="#top"
					>Comprobantes aslkdfjsñldkfjsl asjdñflaksdjfñlkasdjflñi laksdjflskf iasjdñlfkasj
					añslkdfjñaslk añsldkfasl
				</a>
			</li>
			<li><a href="#top">Usuarios</a></li>
			<li><a href="#top">Productos</a></li>
			<li><a href="#top">Clientes</a></li>
			<li><a href="#top">Ofertas</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
			<li><a href="#top">Configuraciones</a></li>
		</ul>
	</nav>
{/if}

<style>
	.nav {
		position: absolute;
		top: 0;
		z-index: 1;
		background-color: var(--main-color);
		max-height: 100%;
		overflow: auto;
		transition: 0.5s;
		text-align: right;
	}
	.menu {
		width: 20rem;
	}
	.menu li {
		margin: 10px;
		text-align: center;
	}
	.menu li a {
		display: inline-block;
		width: 100%;
		padding: 10px;
	}
	.back-button {
		position: sticky;
		top: 0;
		border-radius: 50%;
		padding-bottom: 3px;
	}
</style>
