<script>
	import '../reset.css';
	import Header from './Header.svelte';
	import Nav from './Nav.svelte';

	let activeMenu = false; // boolean

	function toggleMenu() {
		activeMenu = !activeMenu;
	}
	function todayDate() {
		return new Date().toISOString().split('T')[0];
	}
	function searchClient(e) {}
</script>

<!-- *Html -->
<Header on:toggleMenu={toggleMenu} />
<Nav {activeMenu} on:toggleMenu={toggleMenu} />
<main class="center" style="border: 2px solid white;">
	<section class="biller">
		<div class="" style="display: flex; justify-content: space-around;">
			<input type="search" id="search-client" name="search-client" on:keypress={searchClient} />
			<input type="date" name="fecha" id="fecha" value={todayDate()} />
			<select>
				<option value="remito">remito</option>
				<option value="pedido">pedido</option>
				<option value="factura C">factura C</option>
			</select>
			<input type="text" name="num-comprobante" disabled />
		</div>
		<div class="">
			<table>
				<tr>
					<th>Cod. de Barra</th>
					<th>Cantidad</th>
					<th>Item</th>
					<th>Descuento</th>
					<th>Precio</th>
				</tr>
				<tr>
					<td>3874579057126</td>
					<td>2</td>
					<td>Jugo Baggio x1.5L</td>
					<td>10</td>
					<td>1000</td>
				</tr>
			</table>
		</div>
	</section>
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
	}
	.center .biller {
		flex-grow: 1;
		padding: 10px;
	}
	.center aside {
		width: 25%;
	}
</style>
