<script>
	import { Link } from "svelte-routing";
	import { onMount, onDestroy } from "svelte";
	import { fade } from "svelte/transition";
	import { sineIn } from "svelte/easing";
	let y = 0;
	let opacity = 1;
	let openMenu = false;
	let outerWidth = 0;

	$: {
	  if (y < 600) {
		opacity = 1;
	  } else if (y < 850) {
		opacity = 1 - (y - 600) / 100;
	  } else {
		opacity = 0;
	  }
	}

	function toggleMenu() {
		openMenu = !openMenu;
	}
	function closeMenu() {
		openMenu = false;
	}

	function handleClickOutside(event) {
		const nav = document.querySelector(".navbar");
		if (nav && !nav.contains(event.target)) {
			closeMenu();
		}
	}

	onMount(() => {
		document.addEventListener("click", handleClickOutside);
	});

	onDestroy(() => {
		document.removeEventListener("click", handleClickOutside);
	});

  </script>
  
  <nav class="navbar shadow navbar-expand-lg navbar-dark sticky-navbar" style="opacity: {opacity};">
	<div class="container">
		<div class="navbar-header">
		<Link class="logo" to="/">
			<img class="logo-img" src="/logo.png" alt="Logo Icon"/>
		</Link>
		<button class="navbar-toggler more" type="button" on:click={toggleMenu}>
		{#if openMenu}
			<img src="/close.png" alt="Menu Icon" class="transition close-icon" transition:fade={{ delay: 0, duration: 100, easing: sineIn }}/>
		{:else}
			<img src="/more.png" alt="Menu Icon" class="transition more-icon" transition:fade={{ delay: 0, duration: 100, easing: sineIn }}/>
		{/if}
		</button>
		</div>
	  
	  {#if openMenu || outerWidth > 991}
	  <div class="" id="navbarNav">
		<ul class="navbar-nav p-3">
		  <li class="nav-item" id="textRight">
			<Link class="nav-link" to="/">Accueil</Link>
		  </li>
		  <li class="nav-item" id="textRight">
			<Link class="nav-link" to="/projets">Projets</Link>
		  </li>
		  <li class="nav-item" id="textRight">
			<Link class="nav-link" to="/actualites">Actualités</Link>
		  </li>
		  <li class="nav-item" id="textRight">
			<a class="nav-link" href="mailto:astretoulouse@gmail.com?subject=Demande d'information supplémentaires">
			  Nous contacter ✒
			</a>
		  </li>
		</ul>
	  </div>
	  {/if}
	</div>
  </nav>
  
  <style>
	@font-face {
	  font-family: 'Space_grotesk';
	  src: url('/fonts/space_grotesk.ttf') format('truetype');
	  font-weight: normal;
	  font-style: normal;
	}
  
	.sticky-navbar {
	  position: fixed;
	  top: 0;
	  z-index: 1000;
	  width: 100%;
	  overflow-x: hidden;
	  background-color: rgba(0, 0, 0, 0.7);
	  backdrop-filter: blur(10px);
	  -webkit-backdrop-filter: blur(10px);
	  font-family: 'Space_grotesk', sans-serif;
	  font-weight: 600;
	}
	.navbar {
	  padding: 0;
	  width: 100%;
	}
	.container {
	  max-width: 100%;
	}
	.navbar-header {
		display: flex;
		align-items: center;
	}
	.logo-img {
		width: 50px;
		height: 50px;
		margin-top: .8rem;
	}
	.navbar-toggler {
	  padding: 0;
	}
	#navbarNav {
	  display: flex;
	  justify-content: flex-end;
	  flex-grow: 1;
	}
	#textRight {
	  display: flex;
	  justify-content: flex-end;
	  flex-grow: 1;
	}
	.navbar-nav .nav-item .nav-link {
	  color: rgb(255, 255, 255);
	  transition: color 0.3s ease;
	}
	.navbar-nav .nav-item .nav-link:hover {
	  color: #cccccc;
	}
	.more {
		margin-left: auto;
	}
	.close-icon {
		position: absolute;
		top: 1rem;
		right: 1.2rem;
		width: 40px;
		height: 40px;
	}
	.more-icon {
		position: absolute;
		top: .7rem;
		right: .8rem;
		width: 50px;
		height: 50px;
	}

	@media (max-width: 991px) {
		.navbar-header {
			width: 100%;
			justify-content: space-between;
		}
	}

  </style>
  
  <svelte:window bind:scrollY={y} bind:outerWidth/>
  