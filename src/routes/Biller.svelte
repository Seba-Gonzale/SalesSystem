<script>
	import { onMount } from 'svelte';
	import Prueba from './Prueba.svelte';

	let div_propiedades;
	let div_foot;
	let div_detalles;

	let num = Math.trunc(32098000.3498798 * 100) / 100;

	function todayDate() {
		return new Date().toISOString().split('T')[0];
	}

	onMount(() => {
		let div_p_style = getComputedStyle(div_propiedades);
		let div_f_style = getComputedStyle(div_foot);
		let div_p_height = div_p_style.getPropertyValue('height');
		let div_f_height = div_f_style.getPropertyValue('height');
		div_detalles.style.height = `calc(100% - ${div_p_height} - ${div_f_height})`;
	});
</script>

<section class="biller">
	<div class="propiedades" bind:this={div_propiedades}>
		<label
			>Cliente
			<input type="search" id="search-client" name="search-client" value="Consumidor Final" />
		</label>
		<label
			>Fecha
			<input type="date" name="fecha" id="fecha" value={todayDate()} />
		</label>
		<label
			>Tipo
			<select name="tipos-comprobantes">
				<option value="remito">1. Remito</option>
				<option value="pedido">2. Pedido</option>
				<option value="factura C">3. Factura C</option>
			</select>
		</label>
		<label
			>Medio de Pago
			<select name="medio-de-pago">
				<option value="efectivo">1. Efectivo</option>
				<option value="tarjeta">2. Tarjeta</option>
				<option value="transferencia">3. Transferencia</option>
				<option value="qr">4. Código QR</option>
				<option value="cc">5. Cuenta Corriente</option>
			</select>
		</label>
		<label
			>Número
			<textarea
				class="textarea_num-comprobante"
				style="white-space: nowrap; resize: none"
				rows="1"
				type="number"
				name="num-comprobante"
				value="190000000000000000000000000000000000"
				autocomplete="off"
				readonly
				title="Numero de Comprobante"
			/>
		</label>
	</div>

	<div class="detalles" bind:this={div_detalles}>
		<table style="text-align: center; width: 100%;">
			<thead class="thead">
				<tr>
					<th>Cod. de Barra</th>
					<th>Item</th>
					<th>Cantidad</th>
					<th>Desc%</th>
					<th>Precio$</th>
					<th>IVA%</th>
					<th>Subtotal$</th>
				</tr>
			</thead>
			<tbody>
				<Prueba />
			</tbody>
		</table>
	</div>
	<div class="foot" bind:this={div_foot}>
		<div style="display: flex;">
			<div style="flex-grow: 1;">
				<button title="Agregar Item">
					<img src="mas.png" alt="agregar-item" class="icon2" />
				</button>
				<button title="descuento">
					<img src="por-ciento.png" alt="" class="icon2" />
				</button>
				<button title="Cobrar">
					<img src="cobrar.png" alt="cobrar" class="icon2" />
				</button>
			</div>
			<div style="display: flex; align-items: center; font-size: 2rem;">
				Total: <sub style="font-size: 1.2rem; padding: 0 10px;">$</sub>
				{num.toLocaleString()}
			</div>
		</div>
	</div>
</section>

<style>
	.biller {
		flex-grow: 1;
		padding: 10px;
		background-color: var(--main-color);
		overflow: auto;
	}
	.propiedades {
		display: flex;
		flex-wrap: wrap;
	}
	.propiedades > * {
		display: flex;
		flex-direction: column;
		width: 20%;
		margin: 3px;
		padding: 3px;
		text-align: center;
		border-radius: 5px;
	}
	.propiedades label > * {
		height: 2rem;
		font-size: 0.9rem;
		margin-top: 3px;
		padding: 5px;
		background-color: aliceblue;
	}
	.textarea_num-comprobante::-webkit-scrollbar {
		width: 0; /* Ancho de la barra de desplazamiento */
		height: 5px; /* Altura de la barra de desplazamiento horizontal */
	}
	.detalles {
		overflow: auto;
		height: 0px;
		transition: height 0.2s;
	}
	.thead {
		position: sticky;
		top: 0;
		background-color: var(--main-color);
		outline: var(--main-color) solid 1px;
	}
	th {
		font-family: 'Courier New', Courier, monospace;
		padding: 5px;
		vertical-align: middle;
	}
	input:focus,
	select:focus,
	textarea:focus {
		outline: 2px solid red;
		border-color: transparent;
	}
</style>
