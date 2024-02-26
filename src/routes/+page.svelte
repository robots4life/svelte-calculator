<script lang="ts">
	const numbers_1_3 = ['1', '2', '3'];
	const numbers_4_6 = ['4', '5', '6'];
	const numbers_7_9 = ['7', '8', '9'];

	let selectedOperator = '';
	let display: string = '';
	let displayArray: string[] = [];

	let buttonDivide: HTMLButtonElement;
	let buttonMultiply: HTMLButtonElement;

	const handleClear = () => {
		console.log('clear');
		displayArray = [];
		display = '';
		selectedOperator = '';
	};

	const handleNumber = (number: string) => {
		console.log('number : ', number);

		displayArray.push(number);
		display = displayArray.join('');
	};

	const handleOperator = (operator: string) => {
		console.log('operator : ', operator);
		selectedOperator = operator;

		displayArray.push(operator);
		console.log(displayArray);

		display = displayArray.join('');
		console.log(display);

		if (operator === '=') {
			// remove "=" from array
			displayArray.pop();
			console.log('displayArray : ', displayArray);

			let numbers: number[] = [];

			// https://www.typescriptlang.org/docs/handbook/2/objects.html
			// declare Calc interface
			interface Calc {
				numbers: number[];
				operators: string[];
				math: (number | string)[];
			}
			// https://bobbyhadz.com/blog/typescript-type-is-missing-following-properties-from-type
			// specify all required calc object properties
			let calc: Calc = { numbers: [], operators: [], math: [] };
			let numbersIndex: number = 0;
			let operatorsIndex: number = 0;

			displayArray.forEach((element, index, array) => {
				// if string element is a number
				if (!isNaN(parseInt(element))) {
					numbers.push(parseInt(element));
					calc.numbers[numbersIndex] = +numbers.join('');

					// if the last element in the displayArray is iterated
					if (index === array.length - 1) {
						calc.math.push(calc.numbers[calc.numbers.length - 1]);
					}
				}
				// if string element is an operator
				if (isNaN(parseInt(element))) {
					calc.operators[operatorsIndex] = element;

					calc.math.push(calc.numbers[calc.numbers.length - 1]);
					calc.math.push(calc.operators[calc.operators.length - 1]);

					operatorsIndex++;
					numbersIndex++;
					numbers = [];
				}
			});
			console.log('numbers : ', numbers);
			console.log('calc : ', calc);

			let calculationString = Object.values(calc.math).join('');
			console.log('calculationString : ', calculationString);

			let result = eval(calculationString);
			console.log('result : ', result);

			display = result;
		}
	};

	const handleDot = (dot: string) => {
		console.log('dot : ', dot);
		displayArray.push(dot);
	};
</script>

<main>
	<div class="calculator">
		<div class="display">{display}</div>
		<div class="digits">
			<button class="clear span-3" on:click={() => handleClear()}>C</button>
			<button
				bind:this={buttonDivide}
				class="operator divide {selectedOperator === '/' ? 'op-active' : ''}"
				on:click={() => handleOperator('/')}>/</button
			>
			{#each numbers_1_3 as number}
				<button class="number" on:click={() => handleNumber(number)}>{number}</button>
			{/each}
			<button
				bind:this={buttonMultiply}
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
