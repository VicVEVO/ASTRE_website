<script>
	import { Link } from "svelte-routing";
	let y = 0;
	let opacity = 1;
	let openMenu = false;

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
  </script>
  
  <nav class="navbar shadow navbar-expand-lg navbar-dark sticky-navbar" style="opacity: {opacity};">
	<div class="container">
		<div class="navbar-header">
		<Link class="logo" to="/">
			<img class="logo-img" src="/logo.png" alt="Logo Icon"/>
		</Link>
		<button class="navbar-toggler more" type="button" on:click={toggleMenu}>
			<img src="/more.png" alt="Menu Icon" width="40" height="40"/>
		</button>
		</div>
	  
	  {#if openMenu}
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
	  position: -webkit-sticky;
	  position: sticky;
	  top: 0;
	  z-index: 1000;
	  width: 100%;
	  overflow-x: hidden;
	  background-color: rgba(0, 0, 0, 0.2);
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

	@media (max-width: 991px) {
		.sticky-navbar {
			background-color: rgb(2, 2, 2);
		}
		.navbar-header {
			width: 100%;
			justify-content: space-between;
		}
	}

  </style>
  
  <svelte:window bind:scrollY={y} />
  