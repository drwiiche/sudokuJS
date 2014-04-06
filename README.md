#SudokuJS
##JavaScript Sudoku solver

Live demo on: http://jonassebastianohlsson.com/sudoku/

I got interested in sudoku strategies and decided to see whether I could write a solver in JavaScript. This solver currently implements basic strategies, enough to solve (non evil) newspaper sudoku puzzles.

### Basic Usage

#### Initialization
	<script src='sudokuJS.js'></script>
    <link rel='stylesheet' href='sudokuJS.css' />

    <div id='sudoku'></div>

    <script>
	//array representing a standard sudoku puzzle of size 9
	//use space for empty cells
	var board = [
		 , , ,4, ,8, ,2,9
		, , , , , , , , ,4
		,8,5, , ,2, , , ,7
		, , ,8,3,7,4,2, , 
		, ,2, , , , , , , 
		, , ,3,2,6,1,7, , 
		, , , , ,9,3,6,1,2
		,2, , , , , ,4, ,3
		,1,3, ,6,4,2, ,7,undefined
	]
	//NOTE: if last cell is empty, use 'undefined' instead!

    var mySudokuJS = $("#sudoku").sudokuJS({
        board: board
    });
    </script>

#### Solving
	//solves on the board one step at a time.
	mySudokuJS.solveStep();
	//solves the whole board at once
	mySudokuJS.solveAll();
	
### Callbacks
	
#### boardUpdatedFn
Fires whenever the board is updated, whether by user or solver.
Data.cause is either "user input", or name of strategy solver used.
Data.cellsUpdated [] contains the cellIndexes of updated cells.

	 $("#sudoku").sudokuJS({
		board: board
		,boardUpdatedFn: function(data){
			alert("board was updated!");
		}
	});
 

### License
MIT.