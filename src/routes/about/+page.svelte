<script>
	import { onMount } from 'svelte';
	import rock from '$lib/images/rock.svg';
	import leaf from '$lib/images/feuille.svg';
	import cissors from '$lib/images/cissors.svg';
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
  
	.title {
	  font-size: 2rem;
	  color: red;
	  font-style: italic;
	  margin-bottom: 1rem;
	}
  
	.banner {
	  background-color: yellow;
	  padding: 1rem;
	  margin-bottom: 1rem;
	  border-radius: 0.25rem;
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
	  display: flex;
	  align-items: center;
	}
  
	.button img {
	  width: 1.5rem;
	  height: 1.5rem;
	  fill: currentColor;
	  margin-right: 0.5rem;
	}
  
	.result {
	  font-weight: bold;
	  margin-top: 1rem;
	}
  </style>
  
  <div class="container">
	<h1 class="title">Pierre Feuille Ciseaux</h1>
	<div class="banner">
	  <p><em>Choisissez votre coup :</em></p>
	</div>
	<div>
	  <button class="button" on:click={() => playGame('Pierre')}>
		<img src={rock} alt="Rock" />
		<strong>Pierre</strong>
	  </button>
	  <button class="button" on:click={() => playGame('Feuille')}>
		<img src={leaf} alt="Leaf" />
		<strong>Feuille</strong>
	  </button>
	  <button class="button" on:click={() => playGame('Ciseaux')}>
		<img src={cissors} alt="Cissors" />
		<strong>Ciseaux</strong>
	  </button>
	</div>
	{#if playerChoice !== ''}
	  <p>Vous avez choisi : {playerChoice}</p>
	  <p>L'ordinateur a choisi : {computerChoice}</p>
	  <p class="result">Résultat : {result}</p>
	{/if}
</div>  