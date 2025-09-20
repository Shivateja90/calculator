<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled placeholder="0">
        <div class="buttons">
            <button class="btn" data-value="7">7</button>
            <button class="btn" data-value="8">8</button>
            <button class="btn" data-value="9">9</button>
            <button class="btn operator" data-value="/">÷</button>

            <button class="btn" data-value="4">4</button>
            <button class="btn" data-value="5">5</button>
            <button class="btn" data-value="6">6</button>
            <button class="btn operator" data-value="*">×</button>

            <button class="btn" data-value="1">1</button>
            <button class="btn" data-value="2">2</button>
            <button class="btn" data-value="3">3</button>
            <button class="btn operator" data-value="-">−</button>

            <button class="btn" data-value="0">0</button>
            <button class="btn" data-value=".">.</button>
            <button class="btn" id="clear">C</button>
            <button class="btn operator" data-value="+">+</button>

            <button class="btn" id="equals">=</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
/* style.css */
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
}

.calculator {
    background-color: #222;
    padding: 20px;
    border-radius: 10px;
    width: 260px;
}

#display {
    width: 100%;
    height: 50px;
    font-size: 24px;
    text-align: right;
    margin-bottom: 10px;
    padding: 5px;
    border-radius: 5px;
    border: none;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

.btn {
    padding: 20px;
    font-size: 18px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #444;
    color: white;
    transition: 0.2s;
}

.btn:hover {
    background-color: #666;
}

.operator {
    background-color: #ff9500;
}

.operator:hover {
    background-color: #ffa733;
}

#equals {
    grid-column: span 4;
    background-color: #1e90ff;
}

#equals:hover {
    background-color: #3399ff;
}

#clear {
    background-color: #ff3b30;
}

#clear:hover {
    background-color: #ff6659;
}


const display = document.getElementById('display');
const buttons = document.querySelectorAll('.btn');
let currentInput = '';

buttons.forEach(button => {
    button.addEventListener('click', () => {
        const value = button.getAttribute('data-value');

        if (button.id === 'clear') {
            currentInput = '';
            display.value = '';
        } else if (button.id === 'equals') {
            try {
                display.value = eval(currentInput); // simple calculation
                currentInput = display.value;
            } catch {
                display.value = "Error";
            }
        } else {
            currentInput += value;
            display.value = currentInput;
        }
    });
});
