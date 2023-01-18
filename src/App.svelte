<script lang="ts">
  let choiceMade = false
  let wins = 0
  let losses = 0

  const choices = [
    'ROCK',
    'PAPER',
    'SCISSORS',
    'LIZARD',
    'SPOCK'
  ]

  const handleChoice = (choice: string) => {
    choiceMade = true
    evaluateGame(choice)
  }

  const evaluateGame = (choice: string) => {
    const computerChoice = choices[Math.floor(Math.random() * choices.length)]

    // Test the values
    if (choice == 'ROCK') {
      if (computerChoice == 'PAPER') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'SCISSORS') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'ROCK') return calcScore('TIE', choice, computerChoice)
      if (computerChoice == 'LIZARD') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'SPOCK') return calcScore('LOSE', choice, computerChoice)

    }

    if (choice == 'PAPER') {
      if (computerChoice == 'PAPER') return calcScore('TIE', choice, computerChoice)
      if (computerChoice == 'SCISSORS') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'ROCK') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'LIZARD') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'SPOCK') return calcScore('WIN', choice, computerChoice)
    }

    if (choice == 'SCISSORS') {
      if (computerChoice == 'PAPER') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'SCISSORS') return calcScore('TIE', choice, computerChoice)
      if (computerChoice == 'ROCK') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'LIZARD') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'SPOCK') return calcScore('LOSE', choice, computerChoice)
    }

    if (choice == 'LIZARD') {
      if (computerChoice == 'PAPER') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'SCISSORS') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'ROCK') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'LIZARD') return calcScore('TIE', choice, computerChoice)
      if (computerChoice == 'SPOCK') return calcScore('WIN', choice, computerChoice)
    }

    if (choice == 'SPOCK') {
      if (computerChoice == 'PAPER') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'SCISSORS') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'ROCK') return calcScore('WIN', choice, computerChoice)
      if (computerChoice == 'LIZARD') return calcScore('LOSE', choice, computerChoice)
      if (computerChoice == 'SPOCK') return calcScore('TIE', choice, computerChoice)
    }
  }

  const calcScore = (result: string, choice: string, computerChoice: string) => {
    // Set the score based on the result
    switch(result) {
      case 'WIN':
        wins += 1
        alert(`Your choice: ${choice} \nComputer choice: ${computerChoice} \nResult: WIN`)
      break;

      case 'LOSE':
        losses += 1
        alert(`Your choice: ${choice} \nComputer choice: ${computerChoice} \nResult: LOSE`)
      break;

      default:
      alert(`Your choice: ${choice} \nComputer choice: ${computerChoice} \nResult: TIE`)
        break;
    }

    // Reset the flag:
    choiceMade = false
  }

</script>

<main>
  <div>
    <h1>Rock Paper Scissors Lizard Spock
    </h1>
    {#if !choiceMade}
    <p>Please make your choice below:</p>
    {/if}
    <div class="game-container">
      <button class="choice rock" on:click={() => handleChoice('ROCK')}>Rock</button>
      <button class="choice paper" on:click={() => handleChoice('PAPER')}>Paper</button>
      <button class="choice scissors" on:click={() => handleChoice('SCISSORS')}>Scissors</button>
      <button class="choice lizard" on:click={() => handleChoice('LIZARD')}>Lizard</button>
      <button class="choice spock" on:click={() => handleChoice('SPOCK')}>Spock</button>

    </div>
    <div class="scores">
      <p>Wins: {wins}</p>
      <p>Losses: {losses}</p>
    </div>
  </div>
</main>

<style>
  .choice {
    display: flex;
    gap: 30px;
    align-items:center;
    min-height: 100px;
    width: 100%;
    padding: 20px;
  }
  .game-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .rock {
    background-color: #555;
  }

  .paper {
    background-color: #efef;
    color: black;
  }

  .scissors {
    background-color: red;
  }

  .lizard {
    background-color: orange;
  }

  .spock {
    background-color: green;
  }
</style>