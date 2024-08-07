<script>
	import Navbar from "../widget/Navbar.svelte";

</script>

<main>
  <Navbar/>
  <div class="welcome">
    <h1 class="title">
      <strong>Nos projets</strong>
    </h1>
  </div>
  <div class="projects">
    <h2 contenteditable>TOLOSAT</h2>
  </div>
</main>

<style>
  @font-face {
    font-family: 'Space';
    src: url('/fonts/exo2.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
  }

  .welcome {
    position: relative;
    background-image: url('/fond.png');
    background-repeat: repeat;
    background-position: center;
    background-size: cover;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 30rem;
    margin-top: -5rem;
    z-index: 0;
  }

  .title {
    color: #ebebeb;
    font-size: 7rem;
    margin-top: 4rem;
    font-family: 'Space', sans-serif;
    text-shadow: 0px 0px 20px rgba(241,241,241,0.58);
  }

  .projects {
    background-color: rgb(1, 1, 1);
  }

  h2 {
    color: #ebebeb;
    font-family: 'Space', sans-serif;
    text-shadow: 0px 0px 20px rgba(241,241,241,0.58);
    font-size: 120px;
    text-transform: uppercase;
    letter-spacing: -3px;
    transition: 700ms ease;
    font-variation-settings: "wght" 311;
    margin-bottom: 0.8rem;
    outline: none;
    text-align: center;
  }

  h2:hover {
    font-variation-settings: "wght" 582; 
    letter-spacing: 3px;
  }
</style>