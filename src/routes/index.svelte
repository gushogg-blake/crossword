<script>
import {browser} from "$app/env";

let grid = [];
let size = 15;
let mode = "solve";
let direction = "horizontal";

let answers = {
	horizontal: [],
	vertical: [],
};

initGrid();

try {
	grid = JSON.parse(localStorage.getItem("grid"));
	
} catch(e) {
	console.log(e);
}

$: if (browser) {
	localStorage.setItem("grid", JSON.stringify(grid));
}

function initGrid() {
	grid = [];
	
	for (let i = 0; i < size; i++) {
		let row = [];
		
		for (let j = 0; j < size; j++) {
			row.push({
				isLetter: true,
				letter: "",
				x: j,
				y: i,
				
				answer: {
					horizontal: null,
					vertical: null,
				},
				
				answerStart: {
					horizontal: null,
					vertical: null,
				},
			});
		}
		
		grid.push(row);
	}
	
	grid = grid;
}

let hilitedCells = [];

function hilite(cell) {
	
}

function mousedownCell(cell) {
	if (mode === "set") {
		cell.isLetter = !cell.isLetter;
		
		updateNumbers();
		updateAnswers();
		
		grid = grid;
	} else {
		if (document.activeElement === cell.div) {
			console.log("focused");
		}
		
		hilite(cell);
	}
}

function updateAnswers() {
	for (let cell of allCells()) {
		
	}
	for (let cell of allCells()) {
		if (cell.horizontalWordStart) {
			answers.horizontal.push({
				start: cell,
			});
		}
		
		if (cell.verticalWordStart) {
			answers.vertical.push({
				start: cell,
			});
		}
	}
	
	console.log(answers);
}

function *allCells() {
	for (let y = 0; y < size; y++) {
		for (let x = 0; x < size; x++) {
			yield grid[y][x];
		}
	}
}

function updateNumbers() {
	let n = 1;
	
	for (let y = 0; y < size; y++) {
		for (let x = 0; x < size; x++) {
			let cell = grid[y][x];
			let above = grid[y - 1]?.[x]?.isLetter;
			let below = grid[y + 1]?.[x]?.isLetter;
			let left = grid[y][x - 1]?.isLetter;
			let right = grid[y][x + 1]?.isLetter;
			
			if (cell.isLetter && (!above && below || !left && right)) {
				cell.number = n;
				
				n++;
			} else {
				cell.number = null;
			}
		}
	}
	
	grid = grid;
	
	//for (let row of grid) {
	//	for (let cell of row) {
	//		if () {
	//			
	//		}
	//	}
	//}
}

function keydown(e, cell, x, y) {
	let {key} = e;
	let isThereALetter = (cell.letter != '');
	
	if (key.length === 1) {
		cell.letter = key.toUpperCase();
		
		if (direction === "horizontal") {
			if (x + 1 < size) {
				grid[y][x + 1].div.focus();
			}
		} else {
			if (y + 1 < size) {
				grid[y + 1][x].div.focus();
			}
		}
	} else if (key === "Backspace") {
		cell.letter = "";
		
		if (direction === "horizontal") {
			if (x - 1 >= 0) {
				grid[y][x - 1].div.focus();
			}
		} else {
			if (y - 1 >= 0) {
				grid[y - 1][x].div.focus();
			}
		}
	}
	
	grid = grid;
}

function registerDiv(div, [x, y]) {
	grid[y][x].div = div;
}

function debug() {
	console.log(grid);
	console.log(JSON.stringify(grid));
}
</script>

<style type="text/scss">
$cellSize: 36px;
$black: #202020;

#main {
	display: flex;
	flex-direction: column;
	align-items: center;
}

#table {
	display: inline-flex;
	flex-direction: column;
	gap: 1px;
	border: 2px solid $black;
	background: $black;
}

.row {
	display: flex;
	gap: 1px;
}

.cell {
	position: relative;
	display: flex;
	flex-direction: column;
	align-items: center;
	width: $cellSize;
	height: $cellSize;
	outline: none;
}

.cell:focus {
	z-index: 1;
	box-shadow: 0 0 5px 0 black;
}

.cell.isLetter {
	background: white;
}

.cell.hilited {
	background: #00000012;
}

.letter {
	font-size: 18px;
	//width: 100%;
	//height: 100%;
	margin: auto;
}

.number {
	font-size: .8em;
	position: absolute;
	top: 1px;
	left: 1px;
}

#buttons {
	display: flex;
	justify-content: space-between;
}
</style>

<div id="main">
	<div>
		<div id="buttons">
			<div>
				<button on:click={initGrid}>Init</button>
				<button on:click={debug}>debug</button>
				<button on:click={() => mode = mode === "set" ? "solve" : "set"}>{mode}</button>
			</div>
			<div>
				<button on:click={() => direction = direction === "horizontal" ? "vertical" : "horizontal"}>{direction}</button>
			</div>
		</div>
		<br><br>
		<div id="table">
			{#each grid as row, y}
				<div class="row">
					{#each row as cell, x}
						<div
							class="cell"
							class:isLetter={cell.isLetter}
							class:hilited={hilitedCells.includes(cell)}
							tabindex={cell.isLetter ? 0 : null}
							on:keydown={(e) => keydown(e, cell, x, y)}
							on:mousedown={() => mousedownCell(cell)}
							use:registerDiv={[x, y]}
						>
							{#if cell.isLetter}
								{#if cell.number}
									<div class="number">
										{cell.number}
									</div>
								{/if}
								<div class="letter">
									{cell.letter}
								</div>
							{/if}
						</div>
					{/each}
				</div>
			{/each}
		</div>
	</div>
</div>
