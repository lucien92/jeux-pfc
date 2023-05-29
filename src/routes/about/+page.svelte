<script>
	import { onMount } from 'svelte';
	import 'tailwindcss/tailwind.css';
  
	let choices = ['Pierre', 'Feuille', 'Ciseaux'];
	let playerChoice = '';
	let computerChoice = '';
	let result = '';
  
	const playGame = (choice) => {
	  playerChoice = choice;
	  computerChoice = choices[Math.floor(Math.random() * choices.length)];
  
	  if (playerChoice === computerChoice) {
		result = "Égalité !";
	  } else if (
		(playerChoice === 'Pierre' && computerChoice === 'Ciseaux') ||
		(playerChoice === 'Feuille' && computerChoice === 'Pierre') ||
		(playerChoice === 'Ciseaux' && computerChoice === 'Feuille')
	  ) {
		result = "Gagné !";
	  } else {
		result = "Perdu !";
	  }
	};
  </script>
  
  <style>
	.container {
	  display: flex;
	  flex-direction: column;
	  justify-content: center;
	  align-items: center;
	  min-height: 100vh;
	}
  
	.button {
	  padding: 0.5rem 1rem;
	  margin: 0.5rem;
	  border: none;
	  border-radius: 0.25rem;
	  background-color: #4a5568;
	  color: #fff;
	  font-size: 1rem;
	  cursor: pointer;
	}
  </style>
  
  <div class="container">
	<h5>Pierre Feuille Ciseaux</h5>
	<p>Choisissez votre coup :</p>
	<div>
	  <button class="button" on:click={() => playGame('Pierre')}>Pierre</button>
	  <button class="button" on:click={() => playGame('Feuille')}>Feuille</button>
	  <button class="button" on:click={() => playGame('Ciseaux')}>Ciseaux</button>
	</div>
	{#if playerChoice !== ''}
	  <p>Vous avez choisi : {playerChoice}</p>
	  <p>L'ordinateur a choisi : {computerChoice}</p>
	  <p>Résultat : {result}</p>
	{/if}
  </div>
  