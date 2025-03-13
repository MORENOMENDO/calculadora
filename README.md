# calculadora
proyecto I

index.js
import {sum, subtract, multiply, divide} from "./calculator.js"

let output = document.querySelector("#output")

let firstNumber = 0
let operation = null
let resetAfterOperation = false

document.querySelectorAll("#calculator .number").forEach(button => {
    button.addEventListener("click", event => {
        let value = event.currentTarget.textContent
        if (resetAfterOperation) {
            output.value = value
            resetAfterOperation = false
        } else {
            output.value += value
        }
    })
})

document.querySelectorAll("#calculator .operation").forEach(button => {
    button.addEventListener("click", event => {
        firstNumber = Number.parseInt(output.value)
        operation = event.currentTarget.dataset.action
        resetAfterOperation = true
    })
})

const equal = document.querySelector("#calculator .equal")
equal.addEventListener("click", () => {
    if (!operation){
        return
    }
    resetAfterOperation = true
    let secondNumber = Number.parseInt(output.value, 10)

    if (operation === "sum") {
        output.value = sum(firstNumber, secondNumber)
    } else if (operation === "subtract") {
        output.value = subtract(firstNumber, secondNumber)
    } else if (operation === "multiply") {
        output.value = multiply(firstNumber, secondNumber)
    } else if (operation === "divide") {
        output.value = divide(firstNumber, secondNumber)
    }
    //reset operation
    operation = null
})

calculator.js
export function sum(a, b) {
// respuesa
}

export function subtract(a, b) {
// respuesta
}

export function multiply(a, b) {
// respuesta
}

export function divide(a, b) {
// respuesta
}

index.html
<nav class="navbar">
    <h1 class="nav-brand">Calculator</h1>
</nav>

<main class="container">
  <input type="text" id="output" readonly />
  <div id="calculator">
    <button class="number">1</button>
    <button class="number">2</button>
    <button class="number">3</button>
    <button class="operation" data-action="divide"> ÷ </button>
    <button class="number">4</button>
    <button class="number">5</button>
    <button class="number">6</button>
    <button class="operation" data-action="multiply"> × </button>
    <button class="number">7</button>
    <button class="number">8</button>
    <button class="number">9</button>
    <button class="operation" data-action="subtract"> - </button>
    <button class="number zero">0</button>
    <button class="equal"> = </button>
    <button class="operation" data-action="sum"> + </button>
  </div>
</main>

index.css
:root {
  --white: #fff;
  --black: #000;

  /* Primary colors*/
  --primary-1: #D07A1C;
  --primary-2: #E79E4F;
  --primary-3: #E1B98E;
  --primary-4: #F8D9B7;
  --primary-5: #FCF0E3;

  /* Neutral colors */
  --neutral-1: #2c2c2c;
  --neutral-2: #434343;
  --neutral-3: #94868b;
  --neutral-4: #d9cfd3;
  --neutral-5: #f2ecee;

  /* Accent-blue colors */
  --accent-1: #970e3d;
  --accent-2: #c43464;
  --accent-3: #de7699;
  --accent-4: #e6c3ce;
  --accent-5: #fff2f7;
}

body {
  background-color: var(--neutral-5);
  margin: 0;
}

h1 {
  font-size: 36px;
  font-weight: 600;
}

h2 {
  font-size: 28px;
  font-weight: 500;
}

h3 {
  font-size: 24px;
  font-weight: normal;
}

p {
  line-height: 30px;
  font-size: 18px;
}

a {
  color: var(--primary-2);
  font-weight: bold;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}

.rounded {
  border-radius: 30px;
}

.container {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 20px;
}

/* BUTTONS */
.btn {
  border-radius: 3px;
  display: inline-block;
  cursor: pointer;
  font-size: 14px;
  font-weight: 600;
  padding: 13px 40px;
  border: 0;
  transition: background-color 200ms, color 200ms;
}

.btn-default {
  color: var(--white);
  background-color: var(--primary-1);
}

.btn-default:hover,
.btn-outline:hover {
  color: var(--white);
  background-color: var(--primary-2);
  text-decoration: none;
}

.btn-default:active,
.btn-outline:active {
  color: var(--primary-1);
  background-color: var(--primary-4);
}

.btn-default[disabled],
.btn-outline[disabled] {
  color: var(--primary-4);
  background-color: var(--primary-5);
  cursor: default;
}

.btn-accent {
  color: var(--white);
  background-color: var(--accent-1);
}

.btn-accent:hover {
  color: var(--white);
  background-color: var(--accent-2);
  text-decoration: none;
}

.btn-accent:active {
  color: var(--accent-1);
  background-color: var(--accent-4);
}

.btn-accent[disabled] {
  color: var(--accent-4);
  background-color: var(--accent-5);
  cursor: default;
}

.btn-outline {
  color: var(--primary-1);
  background-color: var(--primary-4);
  border: var(--primary-1) 2px solid;
  box-shadow: 1px 1px 7px #c4c4c4;
  padding: 8px 25px;
  border-radius: 10px;
}

/* FORMS */
.form h2 {
  font-size: 24px;
  font-weight: 400;
}

.form h3 {
  font-size: 20px;
  font-weight: 300;
  margin-bottom: 15px;
}

.form-section {
  border-bottom: var(--neutral-4) solid 1px;
  margin-bottom: 20px;
}

.input-required {
  color: var(--primary-2);
  text-decoration: none;
  font-weight: bold;
  padding: 0 1px;
}

.label {
  display: block;
  font-weight: 500;
}

.input {
  font-size: 16px;
  margin-top: 1em;
  margin-bottom: 1.5em;
  padding: 0.75em 0.5em;
  min-width: 200px;
  border: none;
  border-left: 7px solid var(--neutral-4);
  transition: border-left-color 160ms;
  background-color: white;
}

::placeholder {
  color: var(--neutral-3);
}

.input:focus {
  outline: none;
  border-left: 7px solid var(--primary-1);
}

/* NAVBAR */
.navbar {
  background-color: white;
  padding: 10px;
  box-shadow: 0px 3px 7px 1px rgba(0, 0, 0, 0.07),
    0px -3px 7px 1px rgba(0, 0, 0, 0.07);
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 20px;
}

.nav-brand {
  font-weight: 450;
  text-decoration: none;
  padding-left: 20px;
  margin-top: 15px;
  margin-bottom: 15px;
  color: initial;
}

.table {
  width: 100%;
  border-collapse: collapse;
}

.table thead {
  background-color: var(--primary-1);
  color: white;
  border: 1px solid white;
}

.table th {
  padding: 15px;
}
.table td {
  padding: 10px;
}

.table tbody {
  font-size: 18px;
  border: 1px solid white;
}
.table tbody tr:nth-child(2n) {
  background-color: white;
}

.table tbody tr:nth-child(2n + 1) {
  background-color: var(--neutral-5);
}

/*********/

.names-input {
    display: grid;
    grid-template-columns: 1fr 1fr;
}

#output {
    margin-bottom: 20px;
    font-size: 24px;
    outline: none;
    border-radius: 5px;
    padding: 10px 5px;
    border: 0;
}
#calculator {
    display: grid;
    grid-template-columns: repeat(4, 50px);
    grid-template-rows: repeat(4, 50px);
    grid-gap: 10px;
    max-width: 230px;
    background-color: #dcdcdc;
    padding: 15px;
    border-radius: 4px;
}
#calculator button {
    border-radius: 4px;
    outline: none;
    border: 1px solid var(--neutral-3);
}
#calculator button:active {
    background-color: var(--primary-1);
    color: white;
}
.zero {
    grid-column: 1 / span 2;
}
.operation,
.equal {
    font-weight: bold;
    font-size: 16px;
}
