<script>
  let userChoice = null;
  let computerChoice = null;
  let result = null;
  
  const choices = ['Rock', 'Paper', 'Scissors'];
  
  function makeComputerChoice() {
    const randomIndex = Math.floor(Math.random() * choices.length);
    computerChoice = choices[randomIndex];
  }
  
  function determineWinner() {
    if (userChoice === computerChoice) {
      result = "It's a tie!";
    } else if (
      (userChoice === 'Rock' && computerChoice === 'Scissors') ||
      (userChoice === 'Paper' && computerChoice === 'Rock') ||
      (userChoice === 'Scissors' && computerChoice === 'Paper')
    ) {
      result = 'You win!';
    } else {
      result = 'You lose!';
    }
  }
</script>

<main>
  <h1>Rock Paper Scissors</h1>
  
  <div class="choices">
    <button on:click={() => { userChoice = 'Rock'; makeComputerChoice(); determineWinner(); }}>Rock</button>
    <button on:click={() => { userChoice = 'Paper'; makeComputerChoice(); determineWinner(); }}>Paper</button>
    <button on:click={() => { userChoice = 'Scissors'; makeComputerChoice(); determineWinner(); }}>Scissors</button>
  </div>
  
  {#if result}
    <p>You chose {userChoice}, the computer chose {computerChoice}.</p>
    <p>{result}</p>
  {/if}
</main>

<style>
  .choices {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
  }
</style>
