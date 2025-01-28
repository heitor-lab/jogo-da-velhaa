<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jogo da Velha</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        h1 {
            color: #333;
        }
        .board {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: repeat(3, 100px);
            gap: 5px;
            justify-content: center;
            margin: 20px auto;
        }
        .cell {
            width: 100px;
            height: 100px;
            background-color: #fff;
            border: 1px solid #ccc;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            cursor: pointer;
        }
        .cell.taken {
            cursor: not-allowed;
        }
        .message {
            margin: 20px;
            font-size: 1.2rem;
        }
        .reset {
            padding: 10px 20px;
            font-size: 1rem;
            background-color: #007BFF;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .reset:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Jogo da Velha</h1>
    <div class="board" id="board"></div>
    <div class="message" id="message"></div>
    <button class="reset" id="reset">Reiniciar Jogo</button>

    <script>
        const boardElement = document.getElementById('board');
        const messageElement = document.getElementById('message');
        const resetButton = document.getElementById('reset');

        let board = Array(9).fill(null);
        let currentPlayer = 'X';
        let isGameActive = true;

        function renderBoard() {
            boardElement.innerHTML = '';
            board.forEach((cell, index) => {
                const cellElement = document.createElement('div');
                cellElement.classList.add('cell');
                if (cell) {
                    cellElement.textContent = cell;
                    cellElement.classList.add('taken');
                }
                cellElement.addEventListener('click', () => handleCellClick(index));
                boardElement.appendChild(cellElement);
            });
        }

        function handleCellClick(index) {
            if (!isGameActive || board[index]) return;

            board[index] = currentPlayer;
            renderBoard();
            checkWinner();

            currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
            if (isGameActive) {
                messageElement.textContent = `Vez do jogador: ${currentPlayer}`;
            }
        }

        function checkWinner() {
            const winningCombinations = [
                [0, 1, 2], [3, 4, 5], [6, 7, 8],
                [0, 3, 6], [1, 4, 7], [2, 5, 8],
                [0, 4, 8], [2, 4, 6]
            ];

            for (const combination of winningCombinations) {
                const [a, b, c] = combination;
                if (board[a] && board[a] === board[b] && board[a] === board[c]) {
                    messageElement.textContent = `Jogador ${board[a]} venceu!`;
                    isGameActive = false;
                    return;
                }
            }

            if (!board.includes(null)) {
                messageElement.textContent = 'Empate!';
                isGameActive = false;
            }
        }

        resetButton.addEventListener('click', () => {
            board = Array(9).fill(null);
            currentPlayer = 'X';
            isGameActive = true;
            messageElement.textContent = `Vez do jogador: ${currentPlayer}`;
            renderBoard();
        });

        renderBoard();
        messageElement.textContent = `Vez do jogador: ${currentPlayer}`;
    </script>
</body>
</html>
