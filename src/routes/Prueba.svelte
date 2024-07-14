<script>
	let n = 20;
	let html_cantidad = Array(n);
	let html_descuento = Array(n);
	let html_precio = Array(n);

	let cant = Array.from({ length: n }, () => Math.ceil(Math.random() * 10));
	let desc = Array(n).fill(0);
	let precio = Array.from({ length: n }, () => (Math.random() * 1000).toFixed(2));

	function handleOnClick_input(e) {
		e.target.select();
	}
	function handleKeydown_input(e) {
		if (e.key === 'Enter') {
			e.target.blur();
		}
	}

	function handleOnChange_precio(e, p_precio) {
		let value = Math.abs(parseFloat(e.target.value));
		if (isNaN(value)) {
			e.target.style.backgroundColor = 'red';
			return p_precio;
		}

		e.target.style.backgroundColor = '';

		return (e.target.value = value.toFixed(2));
	}

	function handleOnChange_descuento(e) {
		let value = Math.abs(parseFloat(e.target.value));

		if (isNaN(value)) value = 0;
		else if (value > 100) value = 100;

		if (value === 0) e.target.style.color = '';
		else if (value <= 50) e.target.style.color = 'blue';
		else e.target.style.color = 'red';

		return (e.target.value = value);
	}

	function handleOnChange_cantidad(e) {
		let value = parseFloat(e.target.value);

		if (isNaN(value) || value === 0) {
			e.target.style.backgroundColor = 'red';
			e.target.style.color = '';
			return (e.target.value = 0);
		} else {
			if (value <= 0) {
				e.target.style.backgroundColor = '';
				e.target.style.color = 'red';
			} else {
				e.target.style.backgroundColor = '';
				e.target.style.color = '';
			}
		}

		return (e.target.value = value);
	}

	// onMount(() => {
	// 	let div_p_style = getComputedStyle(div_propiedades);
	// 	let div_f_style = getComputedStyle(div_foot);
	// 	let div_p_height = div_p_style.getPropertyValue('height');
	// 	let div_f_height = div_f_style.getPropertyValue('height');
	// 	div_detalles.style.height = `calc(100% - ${div_p_height} - ${div_f_height})`;
	// });
</script>

{#each cant as _, i (i)}
	<tr>
		<td>3874579057126</td>
		<td style="min-width: 30ch;"
			>Jugo Baggio x1.5L {i === 0 ? 'perros de la calle el mejor programa de tv' : ''}</td
		>
		<td style="max-width: 10ch;">
			<input
				name={'cantidad-i' + i}
				type="number"
				step="0.001"
				value={cant[i]}
				on:click={handleOnClick_input}
				on:keydown={handleKeydown_input}
				on:change={(e) => (cant[i] = handleOnChange_cantidad(e))}
				bind:this={html_cantidad[i]}
			/>
		</td>
		<td style="max-width: 10ch;">
			<input
				name={'descuento-i' + i}
				type="number"
				step="0.01"
				min="0"
				max="100"
				value={desc[i]}
				on:click={handleOnClick_input}
				on:keydown={handleKeydown_input}
				on:change={(e) => (desc[i] = handleOnChange_descuento(e))}
				bind:this={html_descuento[i]}
			/>
		</td>
		<td>
			<input
				name={'precio-i' + i}
				type="number"
				step="0.01"
				id="precio"
				value={precio[i]}
				on:click={handleOnClick_input}
				on:keydown={handleKeydown_input}
				on:change={(e) => (precio[i] = handleOnChange_precio(e, precio[i]))}
				bind:this={html_precio[i]}
			/>
		</td>
		<td>
			<select name={'iva-i' + i} on:keydown={handleKeydown_input}>
				<option value="21" selected>21</option>
				<option value="10.5">10.5</option>
			</select>
		</td>
		<td>{(cant[i] * parseFloat(precio[i]) * ((100 - desc[i]) / 100)).toFixed(2)}</td>
	</tr>
{/each}

<style>
	input,
	select {
		width: 100%;
		border: none;
		background-color: transparent;
	}
	input,
	select,
	td {
		font-family: 'Courier New', Courier, monospace;
		font-size: 1rem;
		text-align: center;
	}
	td {
		max-width: 50ch;
		overflow-x: auto;
		white-space: nowrap;
		vertical-align: middle;
		padding: 2px;
		border-left: 2px solid rgba(0, 0, 0, 0.2);
		border-right: 2px solid rgba(0, 0, 0, 0.2);
	}
	td > * {
		padding: 5px;
	}
	tr:nth-child(even) {
		background-color: var(--main-color);
	}
	tr:nth-child(odd) {
		background-color: aliceblue;
	}
	tr:hover {
		outline: black solid 2px;
	}
	td::-webkit-scrollbar {
		width: 0; /* Ancho de la barra de desplazamiento */
		height: 5px; /* Altura de la barra de desplazamiento horizontal */
	}
	select {
		min-width: 8ch;
	}
</style>
