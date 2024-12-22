<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Number Guessing Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      margin: 20px;
    }
    input {
      padding: 10px;
      font-size: 16px;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }
    .message {
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <h1>Number Guessing Game</h1>
  <p>Guess the number between 1 and 100!</p>
  <input type="number" id="guessInput" placeholder="Enter your guess">
  <button onclick="checkGuess()">Guess</button>
  <div class="message" id="message"></div>

  <script>
    const numberToGuess = Math.floor(Math.random() * 100) + 1;
    let attempts = 0;
    const maxAttempts = 10;

    function checkGuess() {
      const userGuess = parseInt(document.getElementById("guessInput").value, 10);
      const messageElement = document.getElementById("message");
      attempts++;

      if (isNaN(userGuess)) {
        messageElement.textContent = "Please enter a valid number!";
        return;
      }

      if (userGuess < numberToGuess) {
        messageElement.textContent = `Too low! Attempts left: ${maxAttempts - attempts}`;
      } else if (userGuess > numberToGuess) {
        messageElement.textContent = `Too high! Attempts left: ${maxAttempts - attempts}`;
      } else {
        messageElement.textContent = `Congratulations! You guessed the number ${numberToGuess} in ${attempts} attempts.`;
        return;
      }

      if (attempts >= maxAttempts) {
        messageElement.textContent = `Game over! The number was ${numberToGuess}.`;
        document.getElementById("guessInput").disabled = true;
      }
    }
  </script>
</body>
</html>
