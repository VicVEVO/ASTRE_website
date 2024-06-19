<!-- App.svelte -->
<script>
	import { Router, Route } from "svelte-routing";
	import Index from "./views/Index.svelte";
  import Projets from "./views/Projets.svelte";
  import Actualites from "./views/Actualites.svelte";
  
	export let url = "";
  </script>
  <Router url="{url}">
	<Route path="/" component="{Index}" />
	<Route path="/projets" component="{Projets}" />
	<Route path="/actualites" component="{Actualites}" />
  </Router>
  