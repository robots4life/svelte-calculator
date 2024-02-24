<script lang="ts">
	const numbers_1_3 = ['1', '2', '3'];
	const numbers_4_6 = ['4', '5', '6'];
	const numbers_7_9 = ['7', '8', '9'];

	const handleNumber = (number: string) => {
		console.log('number : ', number);
	};

	const handleOperator = (operator: string) => {
		console.log('operator : ', operator);
	};
</script>

<main>
	<div class="calculator">
		<div class="display">123</div>
		<div class="digits">
			<button class="clear span-3">C</button>
			<button class="operator divide" data-operator={'/'} on:click={() => handleOperator('/')}
				>/</button
			>

			{#each numbers_1_3 as number}
				<button
					class="number"
					id={number}
					data-number={number}
					on:click={() => handleNumber(number)}>{number}</button
				>
			{/each}

			<button class="operator multiply" data-operator={'*'}>*</button>

			{#each numbers_4_6 as number}
				<button
					class="number"
					id={number}
					data-number={number}
					on:click={() => handleNumber(number)}>{number}</button
				>
			{/each}

			<button class="operator subtract" data-operator={'-'}>-</button>

			{#each numbers_7_9 as number}
				<button
					class="number"
					id={number}
					data-number={number}
					on:click={() => handleNumber(number)}>{number}</button
				>
			{/each}

			<button class="operator add" data-operator={'+'}>+</button>
			<button class="number span-2" id="0" data-number="0">0</button>
			<button class="dot" data-dot=".">.</button>
			<button class="operator equal" data-operator={'='}>=</button>
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
</style>
