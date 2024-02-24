<script lang="ts">
	const numbers_1_3 = ['1', '2', '3'];
	const numbers_4_6 = ['4', '5', '6'];
	const numbers_7_9 = ['7', '8', '9'];

	let display = '';
	let selectedOperator = '';

	const handleClear = () => {
		console.log('clear');
		display = '';
	};

	const handleNumber = (number: string) => {
		console.log('number : ', number);
		display = `${display}${number}`;
	};

	const handleOperator = (operator: string) => {
		console.log('operator : ', operator);
		selectedOperator = operator;
		console.log('selectedOperator : ', selectedOperator);
	};

	const handleDot = (dot: string) => {
		console.log('dot : ', dot);
	};
</script>

<main>
	<div class="calculator">
		<div class="display">{display}</div>
		<div class="digits">
			<button class="clear span-3" on:click={() => handleClear()}>C</button>
			<button
				class="operator divide {selectedOperator === '/' ? 'op-active' : ''}"
				on:click={() => handleOperator('/')}>/</button
			>
			{#each numbers_1_3 as number}
				<button class="number" on:click={() => handleNumber(number)}>{number}</button>
			{/each}
			<button
				class="operator multiply {selectedOperator === '*' ? 'op-active' : ''}"
				on:click={() => handleOperator('*')}>*</button
			>
			{#each numbers_4_6 as number}
				<button class="number" on:click={() => handleNumber(number)}>{number}</button>
			{/each}
			<button
				class="operator subtract {selectedOperator === '-' ? 'op-active' : ''}"
				on:click={() => handleOperator('-')}>-</button
			>
			{#each numbers_7_9 as number}
				<button class="number" on:click={() => handleNumber(number)}>{number}</button>
			{/each}
			<button
				class="operator add {selectedOperator === '+' ? 'op-active' : ''}"
				on:click={() => handleOperator('+')}>+</button
			>
			<button class="number span-2" on:click={() => handleNumber('0')}>0</button>
			<button class="dot" on:click={() => handleDot('.')}>.</button>
			<button
				class="operator equal {selectedOperator === '=' ? 'op-active' : ''}"
				on:click={() => handleOperator('=')}>=</button
			>
		</div>
	</div>
</main>

<style>
	.calculator {
		width: 100%;
	}
	.display {
		display: flex;
		align-items: center;
		justify-content: end;
		padding-right: 0.4rem;
		width: 100%;
		height: 4rem;
		font-size: 2rem;
		font-weight: bold;
		font-family: sans-serif;
		letter-spacing: 0.2rem;
		background-color: lightslategrey;
		color: white;
		border-radius: 12px;
		margin-bottom: 1rem;
	}
	.digits {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 1rem;
	}
	.span-2 {
		grid-column: span 2;
	}
	.span-3 {
		grid-column: span 3;
	}
	button {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 4rem;
		font-size: 2rem;
		border: 2px solid black;
		border-radius: 12px;
	}
	.operator {
		font-size: 3rem;
		font-weight: bold;
		background-color: orange;
	}
	.op-active {
		background-color: aqua;
	}
</style>
