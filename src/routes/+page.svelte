<script>
	import { onMount } from 'svelte';
	import 'tailwindcss/tailwind.css';
	import { ProgressBar } from '@prgm/sveltekit-progress-bar'

	let isTextVisible = false;
	let isLoading = true;
  
	onMount(() => {
	  setTimeout(() => {
		isTextVisible = true;
		isLoading = false;
	  }, 500);
	});

	import { afterUpdate } from 'svelte';

	onMount(() => {
		// Simuler un délai de chargement
		setTimeout(() => {
		isLoading = false;
		}, 2000);
	});

	afterUpdate(() => {
		if (!isLoading) {
		// Supprimer la barre de chargement une fois que la page est chargée
		document.getElementById('loading-bar').remove();
		}
	});
  </script>
  
  <style>
	
	.container {
	  display: flex;
	  flex-direction: column;
	  justify-content: center;
	  min-height: 100vh;
	  background-image: url('image_fond.jpeg');
	  background-size: cover;
	}
  
	.text {
	  font-size: 24px;
	  text-align: center;
	  color: black;
	  font-weight: bold;
	  opacity: 0;
	  transition: opacity 500ms ease-in-out;
	  white-space: nowrap;
	  overflow: hidden;
	}
  
	.text-visible {
	  opacity: 1;
	  transition-delay: 500ms;
	}
  
	.loading-bar {
		width: 100%;
		height: 40px;
		background-color: black;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 9999;
	}

	.loading-bar-progress {
		width: 0%;
		height: 100%;
		background-color: black;
		transition: width 0.3s ease;
		display: flex;
		justify-content: center;
		align-items: center;
		color: black;
		font-weight: bold;
		font-size: 16px;
	}

  </style>

  <div class="loading-bar" id="loading-bar">
	<div class="loading-bar-progress" style="width: 100%;">
	  <ProgressBar />
  </div>
  </div>
  
  <div class="container">
	
	
	<h1 class="text transition-opacity duration-500 ease-in-out delay-500" class:text-visible={isTextVisible}>
	  <span class="animate-appear-letter">
		Pierre Feuille Ciseaux
	  </span>
	</h1>
	<p class="text transition-opacity duration-500 ease-in-out delay-1000" class:text-visible={isTextVisible}>
	  <span class="animate-appear-letter">
		Pierre-papier-ciseaux est un jeu effectué avec les mains et opposant deux joueurs.
	  </span>
	</p>
	<p class="text transition-opacity duration-1000 ease-in-out delay-1500" class:text-visible={isTextVisible}>
	  <span class="animate-appear-letter">
		Il possède de nombreux noms alternatifs, notamment en variant l'ordre des termes
	  </span>
	</p>
	<p class="text transition-opacity duration-1500 ease-in-out delay-2000" class:text-visible={isTextVisible}>
	  <span class="animate-appear-letter">
		ou en remplaçant certains mots comme « papier » par « feuille » ou « pierre » par
	  </span>
	</p>
	<p class="text transition-opacity duration-25000 ease-in-out delay-30000" class:text-visible={isTextVisible}>
	  <span class="animate-appear-letter">
		« caillou » ou « roche ». Le terme chifoumi est également une appellation courante.
	  </span>
	</p>
  </div>
