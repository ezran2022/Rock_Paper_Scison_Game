# Rock_Paper_Scison_Game
## This is the game of chance

We just give you a poosibility of playing against computer by choosing among three option
if player choice is equal to computer choice it is draw game 
and if player choice is equal to Rock and Computer choice is equal to Scissors or player choice is equal to Paper and Computer choice is equal to Rock 
or player choice is equal to Scissors and Computer choice is equal to Paper here you win the game 
else you loose the game

As you see the player win against the computer


![image](https://user-images.githubusercontent.com/103323625/185881343-67455dc5-4a42-4486-b223-d56b90a5b7cf.png)


![image](https://user-images.githubusercontent.com/103323625/185881498-bd8c267a-f1cf-4ef9-b8ac-0ab56845eedb.png)

Now it is Draw game

![image](https://user-images.githubusercontent.com/103323625/185881709-1bb656a1-104f-4411-bbd1-6d907ce86321.png)

Now you loose because it does not match the condition of winning

![image](https://user-images.githubusercontent.com/103323625/185881960-510571fd-7d82-4fca-9e21-e029feb685f1.png)


## This is how this app work!!!

### Link
https://poetic-clafoutis-e8f779.netlify.app

### code
``` javascript


// ** getComputerChoice randomly selects between `rock` `paper` `scissors` and returns that string **
// getComputerChoice() 👉 'Rock'
// getComputerChoice() 👉 'Scissors'
function getComputerChoice() {
    let rpsChoices = ['Rock', 'Paper', 'Scissors']
    let computerChoice = rpsChoices[Math.floor(Math.random() * 3)]
    return computerChoice
  }
  
  // ** getResult compares playerChoice & computerChoice and returns the score accordingly **
  // human wins - getResult('Rock', 'Scissors') 👉 1
  // human loses - getResult('Scissors', 'Rock') 👉 -1
  // human draws - getResult('Rock', 'Rock') 👉 0
  function getResult(playerChoice, computerChoice) {
    // return the result of score based on if you won, drew, or lost
    
    let score;
  
    // All situations where human draws, set `score` to 0
    if (playerChoice === computerChoice) {
      score = 0
  
    
    } else if (playerChoice === 'Rock' && computerChoice === 'Scissors') {
      score = 1
  
    } else if (playerChoice === "Paper" && computerChoice === "Rock") {
      score = 1
  
    } else if (playerChoice === "Scissors" && computerChoice === "Paper") {
      score = 1
  
    // Otherwise human loses (aka set score to -1)
    } else {
      score = -1
    }
  
    // return score
    return score
  }
  
  // ** showResult updates the DOM to `You Win!` or `You Lose!` or `It's a Draw!` based on the score. Also shows Player Choice vs. Computer Choice**
  function showResult(score, playerChoice, computerChoice) {
    // Hint: on a score of -1
    // You should do result.innerText = 'You Lose!'
    // Don't forget to grab the div with the 'result' id!
    
    let result = document.getElementById('result')
    switch (score) {
      case -1:
        result.innerText = `You Lose!`
        break;
      case 0:
        result.innerText = `It's a Draw!`
        break;
      case 1:
        result.innerText = `You Win!`
        break;
    }
  
    let playerScore = document.getElementById('player-score')
    let hands = document.getElementById('hands')
    playerScore.innerText = `${Number(playerScore.innerText) + score}`
      hands.innerText = `👱 ${playerChoice} vs 🤖 ${computerChoice}`
  }
  
  // ** Calculate who won and show it on the screen **
  function onClickRPS(playerChoice) {
    const computerChoice = getComputerChoice()
    const score = getResult(playerChoice.value, computerChoice)
    showResult(score, playerChoice.value, computerChoice)
  }
  
  // ** Make the RPS buttons actively listen for a click and do something once a click is detected **
  function playGame() {
    // use querySelector to select all RPS Buttons
    let rpsButtons = document.querySelectorAll('.rpsButton')
  
    // * Adds an on click event listener to each RPS button and every time you click it, it calls the onClickRPS function with the RPS button that was last clicked *
    
    // 1. loop through the buttons using a forEach loop
    // 2. Add a 'click' event listener to each button
    // 3. Call the onClickRPS function every time someone clicks
    // 4. Make sure to pass the currently selected rps button as an argument
  
    rpsButtons.forEach(rpsButton => {
      rpsButton.onclick = () => onClickRPS(rpsButton)
    })
  
    // Add a click listener to the end game button that runs the endGame() function on click
    let endGameButton = document.getElementById('endGameButton')
    endGameButton.onclick = () => endGame()
  }
  
  // ** endGame function clears all the text on the DOM **
  function endGame() {
    let playerScore = document.getElementById('player-score')
    let hands = document.getElementById('hands')
    let result = document.getElementById('result')
    playerScore.innerText = ''
    hands.innerText = ''
    result.innerText = ''
  }
  
  playGame()

```
