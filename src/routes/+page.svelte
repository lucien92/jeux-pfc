<script>
	import { onMount } from 'svelte';
	import 'tailwindcss/tailwind.css';
	let isTextVisible = false;
  
	onMount(() => {
	  setTimeout(() => {
		isTextVisible = true;
	  }, 500);
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
  </style>
  
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
		« caillou » ou « roche ». Le terme chifoumi est également une appellation courante.		</span>
	</p>
  </div>
  
  