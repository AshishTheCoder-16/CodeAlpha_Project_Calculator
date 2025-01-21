# CodeAlpha_Project_Calculator
# A fully functional and responsive calculator website built using HTML, CSS, and JavaScript. This project provides a clean and intuitive user interface for performing basic arithmetic operations such as addition, subtraction, multiplication, and division.

#Progra Of The Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }

        .calculator {
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            width: 300px;
        }

        .display {
            width: 100%;
            height: 60px;
            background: #222;
            color: #fff;
            text-align: right;
            padding: 10px;
            font-size: 2rem;
            border-radius: 5px;
            margin-bottom: 15px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            height: 60px;
            font-size: 1.5rem;
            background: #007bff;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        button:hover {
            background: #0056b3;
        }

        .operator {
            background: #28a745;
        }

        .operator:hover {
            background: #1e7e34;
        }

        .clear {
            background: #dc3545;
        }

        .clear:hover {
            background: #c82333;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="clear" id="clear">C</button>
            <button class="operator" id="divide">/</button>
            <button class="operator" id="multiply">*</button>
            <button class="operator" id="subtract">-</button>
            <button>7</button>
            <button>8</button>
            <button>9</button>
            <button class="operator" id="add">+</button>
            <button>4</button>
            <button>5</button>
            <button>6</button>
            <button>1</button>
            <button>2</button>
            <button>3</button>
            <button class="equals" id="equals">=</button>
            <button>0</button>
            <button>.</button>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const display = document.getElementById('display');
            const buttons = document.querySelectorAll('button');
            let currentInput = '';
            let previousInput = '';
            let operator = '';

            buttons.forEach(button => {
                button.addEventListener('click', () => {
                    const value = button.textContent;

                    if (value >= '0' && value <= '9' || value === '.') {
                        currentInput += value;
                        display.textContent = currentInput;
                    } else if (value === 'C') {
                        currentInput = '';
                        previousInput = '';
                        operator = '';
                        display.textContent = '0';
                    } else if (value === '=') {
                        if (currentInput && previousInput && operator) {
                            currentInput = eval(`${previousInput} ${operator} ${currentInput}`).toString();
                            display.textContent = currentInput;
                            previousInput = '';
                            operator = '';
                        }
                    } else {
                        if (currentInput) {
                            previousInput = currentInput;
                            currentInput = '';
                            operator = value;
                        }
                    }
                });
            });
        });
    </script>
</body>
</html>
