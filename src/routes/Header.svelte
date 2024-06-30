<script>
	import { createEventDispatcher } from 'svelte';

	let dispatch = createEventDispatcher();

	function toggleMenu() {
		dispatch('toggleMenu');
	}

	let icons = [
		'comprobantes.png',
		'clientes.png',
		'equipo.png',
		'productos.png',
		'ofertas.png',
		'configuracion.png'
	];
	// let iconsTitle = array.map(() => {});
</script>

<header class="header">
	<button on:click={toggleMenu} class="header-left" src="menu.png" title="menu"
		><img src="menu.png" alt="menu" class="icon" /></button
	>
	<div class="header-center">
		{#each icons as icon}
			<button title={icon.slice(0, icon.indexOf('.png'))}
				><img src={icon} alt={icon.slice(0, icon.indexOf('.png'))} class="icon" /></button
			>
		{/each}
	</div>
	<button class="header-right" src="iniciar-sesion.png" alt="Iniciar sesion" title="Iniciar sesion"
		><img src="iniciar-sesion.png" alt="iniciar sesion" class="icon" /></button
	>
</header>

<style>
	.header {
		position: sticky;
		top: 0;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		background-color: var(--main-color);
	}
	.header > * {
		display: flex;
		align-items: center;
	}
	/* .header-center button {
		padding-bottom: 4px;
	} */
	.header-center {
		flex-grow: 1;
		align-items: center;
		justify-content: center;
	}

	/* .header-center > button {
		height: 32px;
	} */

	/* .header-left {
	}
	.header-right {
	} */
</style>
