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
	<nav class="nav" transition:slide={{ axis: 'x' }}>
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
		padding-bottom: 4px;
		background-color: var(--main-color);
	}
	.back-button .icon {
		filter: contrast(80%);
	}
	.back-button:hover .icon {
		filter: inherit;
	}
	.back-button:hover {
		border: 2px solid white;
	}

	/* Estilo para la barra de desplazamiento en navegadores WebKit */
	.nav::-webkit-scrollbar {
		width: 12px; /* Ancho de la barra de desplazamiento */
		height: 12px; /* Altura de la barra de desplazamiento horizontal */
	}

	/* Estilo para la pista de la barra de desplazamiento */
	.nav::-webkit-scrollbar-track {
		background: whitesmoke; /* Color de fondo de la pista */
		border-radius: 6px; /* Bordes redondeados */
	}

	/* Estilo para el controlador de la barra de desplazamiento */
	.nav::-webkit-scrollbar-thumb {
		background-color: cadetblue; /* Color del controlador */
		border-radius: 6px; /* Bordes redondeados */
	}

	/* Estilo para el controlador de la barra de desplazamiento al pasar el cursor */
	.nav::-webkit-scrollbar-thumb:hover {
		background-color: cornflowerblue; /* Color del controlador al pasar el cursor */
	}
</style>
