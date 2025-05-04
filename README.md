<!DOCTYPE html>
<html>
<head>
<title>Ramble Words Game</title>
</head>
<style>
body{ 
  text-align:center;
}
</style>
<body>
  <h1>Ramble Words</h1>
  <p id="ramble-word"></p>
  <input type="text" id="user-guess" placeholder="Enter your guess">
  <button onclick="checkGuess()">Check</button>
  <p id="result"></p>

  <script>
    let words = ["Pneumonoultramicroscopicsilicovolcanoconiosis", "javascript", "programming", "computer", "science", "algorithm"];

    let currentWord;
    let scrambledWord;

    function shuffleWord(word) {
      let letters = word.split("");
      for (let i = letters.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [letters[i], letters[j]] = [letters[j], letters[i]];
      }
      return letters.join("");
    }

    function startGame() {
      let randomIndex = Math.floor(Math.random() * words.length);
      currentWord = words[randomIndex];
      scrambledWord = shuffleWord(currentWord);
      document.getElementById("ramble-word").innerHTML = scrambledWord;
      document.getElementById("user-guess").value = ""; 
      document.getElementById("result").innerHTML = ""; 
    }

    function checkGuess() {
      let userGuess = document.getElementById("user-guess").value.toLowerCase();

      if (userGuess === currentWord) {
        alert("Correct! You win!");
      } else {
        alert("Incorrect. The word was " + currentWord + ".");


      }
    }

    startGame(); 
  </script>
</body>
</html>
