<!-- src/components/GuessingGame.vue -->
<template>
    <div class="guessing-game">
      <h1>Guess the Number Game</h1>
      <p v-if="remainingAttempts > 0">Guess the number between 1 and 100:</p>
      <p v-else>The number was {{ targetNumber }}. Better luck next time!</p>
      
      <input 
        type="number" 
        v-model="userGuess" 
        :disabled="remainingAttempts === 0"
        @keypress="validateInput"
        placeholder="Enter your guess" 
      />
      
      <button @click="makeGuess" :disabled="remainingAttempts === 0 || userGuess === ''">Submit Guess</button>
      
      <p v-if="message">{{ message }}</p>
      <p>Remaining Attempts: {{ remainingAttempts }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        targetNumber: Math.floor(Math.random() * 100) + 1,
        userGuess: '',
        remainingAttempts: 3,
        message: ''
      };
    },
    methods: {
      makeGuess() {
        const guess = parseInt(this.userGuess, 10);
        if (guess < this.targetNumber) {
          this.message = 'Too low!';
        } else if (guess > this.targetNumber) {
          this.message = 'Too high!';
        } else {
          this.message = 'Congratulations! You guessed it right!';
          this.remainingAttempts = 0;
          return;
        }
        this.remainingAttempts--;
        if (this.remainingAttempts === 0 && guess !== this.targetNumber) {
          this.message = `Game over! The number was ${this.targetNumber}.`;
        }
        this.userGuess = '';
      },
      validateInput(event) {
        const char = String.fromCharCode(event.keyCode);
        if (!/[0-9]/.test(char)) {
          event.preventDefault();
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .guessing-game {
    max-width: 400px;
    margin: 50px auto;
    text-align: center;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 10px;
    background-color: #f9f9f9;
  }
  
  input[type="number"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
    font-size: 16px;
  }
  
  button {
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
  }
  
  p {
    font-size: 16px;
  }
  </style>
  