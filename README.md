# Svelte Calculator

#### 1. Create markup and styles

```html
<main>
	<div class="calculator">
		<div class="display">123</div>
		<div class="digits">
			<button class="clear span-3">C</button>
			<button class="operator divide">/</button>
			<button class="number">1</button>
			<button class="number">2</button>
			<button class="number">3</button>
			<button class="operator multiply">*</button>
			<button class="number">4</button>
			<button class="number">5</button>
			<button class="number">6</button>
			<button class="operator subtract">-</button>
			<button class="number">7</button>
			<button class="number">8</button>
			<button class="number">9</button>
			<button class="operator add">+</button>
			<button class="number span-2">0</button>
			<button class="dot">.</button>
			<button class="operator equal">=</button>
		</div>
	</div>
</main>
```

```css
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
```

#### 2. Iterate over numbers with each

```ts
const numbers_1_3 = ['1', '2', '3'];
const numbers_4_6 = ['4', '5', '6'];
const numbers_7_9 = ['7', '8', '9'];
```

<!-- prettier-ignore -->
```html
{#each numbers_1_3 as number}
	<button class="number" id="{number}">{number}</button>
{/each}
```

#### 3. Handle calculator buttons
