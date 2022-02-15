<script>
let grid = [];
let size = 13;
let mode = "solve";

grid = [[{"isLetter":true,"letter":"","number":1},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":2},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":3},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":4},{"isLetter":true,"letter":"","number":5},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":6}],[{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":7},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":8},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":9},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":10},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":11},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":12},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":13},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":14},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":15},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":16}],[{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":17},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":18},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":19},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":20},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":21},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":22},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}],[{"isLetter":true,"letter":"","number":23},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":false,"letter":"","number":null},{"isLetter":true,"letter":"","number":24},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null},{"isLetter":true,"letter":"","number":null}]];

function initGrid() {
	grid = [];
	
	for (let i = 0; i < size; i++) {
		let row = [];
		
		for (let j = 0; j < size; j++) {
			row.push({
				isLetter: true,
				letter: "",
			});
		}
		
		grid.push(row);
	}
	
	grid = grid;
}

function clickCell(cell) {
	if (mode !== "set") {
		return;
	}
	
	cell.isLetter = !cell.isLetter;
	
	grid = grid;
}

function addNumbers() {
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

function keydown(e, cell) {
	let {key} = e;
	
	if (key.length === 1) {
		cell.letter = key.toUpperCase();
	}
	
	grid = grid;
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
</style>

<div id="main">
	<div>
		<button on:click={initGrid}>Init</button>
		<button on:click={addNumbers}>Add numbers</button>
		<button on:click={debug}>Debug</button>
	</div>
	<br><br>
	<div id="table">
		{#each grid as row, y}
			<div class="row">
				{#each row as cell, x}
					<div
						class="cell"
						class:isLetter={cell.isLetter}
						tabindex="0"
						on:keydown={(e) => keydown(e, cell)}
						on:click={() => clickCell(cell)}
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
