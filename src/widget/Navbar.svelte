<script>
	import { Link } from "svelte-routing";
	let y = 0;
	let opacity = 1;
  
	$: {
	  if (y < 600) {
		opacity = 1;
	  } else if (y < 850) {
		opacity = 1 - (y - 600) / 100;
	  } else {
		opacity = 0;
	  }
	}
  </script>
  
  <nav class="navbar shadow navbar-expand-lg navbar-dark sticky-navbar" style="opacity: {opacity};">
	<div class="container">
	  <Link class="navbar-brand" to="/">
		<img class="img-fluid logo-img" src="/logo.png" alt="bootstrap svelte"/>
	  </Link>
	  <button class="navbar-toggler btn rounded-circle" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
		<img src="/menu-icon.png" alt="Menu Icon" width="26" height="26"/>
	  </button>
	  <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
		<ul class="navbar-nav p-3">
		  <li class="nav-item">
			<Link class="nav-link" to="/">Home</Link>
		  </li>
		  <li class="nav-item">
			<Link class="nav-link" to="/projets">Projets</Link>
		  </li>
		  <li class="nav-item">
			<Link class="nav-link" to="/actualites">Actualités</Link>
		  </li>
		  <li class="nav-item">
			<a class="nav-link" href="https://www.hockeycomputindo.com/2021/10/svelte-bootstrap-free-download-source.html">
			  Nous contacter →
			</a>
		  </li>
		</ul>
	  </div>
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
	  padding: 0 300px;
	}
	.logo-img {
	  width: 50px;
	  height: auto;
	}
	.navbar-toggler {
	  padding: 0;
	}
	.navbar-nav .nav-item .nav-link {
	  color: rgb(255, 255, 255);
	  transition: color 0.3s ease;
	}
	.navbar-nav .nav-item .nav-link:hover {
	  color: #cccccc;
	}
  </style>
  
  <svelte:window bind:scrollY={y} />
  