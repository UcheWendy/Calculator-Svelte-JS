<script>
let answer = '';
let currentNumber = '';
function evaluateExpression(expression) {
  try {
    const answer = Function(`'use strict'; return (${expression})`)();
    return answer;
  } catch (error) {
    return 'Error';
  }
}

function handleClick(value) {

  if (value === '=') {
    answer = evaluateExpression(answer);
  }  else if (value === 'Clear Entry') {
    currentNumber = '';
    answer = ''; 
 } else {
    currentNumber += value;
    answer += value;
  }
}

  function clearCalculator() {
    answer = '';
    currentNumber = '';
  }
</script>

<div class="text-column calculator">
  <input type="text" value={answer} readonly />

  <div class="buttons">
<button  class="clearButton" on:click={() => clearCalculator()}>Clear Entry</button>
    <button class="ArithmeticButton" on:click={() => handleClick('/')}>/</button>
    <button on:click={() => handleClick('7')}>7</button>
    <button on:click={() => handleClick('8')}>8</button>
    <button on:click={() => handleClick('9')}>9</button>
    <button class="ArithmeticButton" on:click={() => handleClick('*')}>*</button>
    <button on:click={() => handleClick('4')}>4</button>
    <button on:click={() => handleClick('5')}>5</button>
    <button on:click={() => handleClick('6')}>6</button>
    <button class="ArithmeticButton" on:click={() => handleClick('-')}>-</button>
    <button on:click={() => handleClick('1')}>1</button>
    <button on:click={() => handleClick('2')}>2</button>
    <button on:click={() => handleClick('3')}>3</button>
    <button class="ArithmeticButton" on:click={() => handleClick('+')}>+</button>
    <button on:click={() => handleClick('0')}>0</button>
    <button on:click={() => handleClick('.')}>.</button>
    <button class="equalsButton" on:click={() => handleClick('=')}>=</button>
  </div>
</div>

<style>
  .calculator {
    display: grid;
    gap: 5px;
    padding: 10px;
    background-color: #d3d3d3;
    border: 1px solid #d3d3d3;
    border-radius: 5px;
  }

  input[type="text"] {
    padding: 10px;
    font-size: 1.5rem;
    text-align: right;
    border: none; 
    outline: none;
  }

  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 5px;
  }

  button {
    padding: 10px;
    font-size: 1.5rem;
    background-color: white;
    border: 1px solid #ccc;
    border-radius: 5px;
    cursor: pointer;
  }
.clearButton {
color: red;  
}
 
  button:hover {
    background-color: #f2f2f2;
  }
</style>