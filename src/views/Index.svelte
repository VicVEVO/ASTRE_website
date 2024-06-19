<script>
  import Navbar from "../widget/Navbar.svelte";
  import { onMount } from 'svelte';

  let video, background0;

  const handleScroll = () => {
    const scrollPosition = window.scrollY;
    const parallaxSpeed = -0.1;
    video.style.transform = `translateY(${scrollPosition * parallaxSpeed}px)`;
    background0.style.transform = `translateY(${scrollPosition * parallaxSpeed / 2}px)`;
  };

  onMount(() => {
    window.addEventListener('scroll', handleScroll);
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>
  
<main>
  <Navbar />

  <div class="part-0">
    <div class="background-0" bind:this={background0}></div>
    <div class="content">
      <h1 class="text-white small">
        <strong>Association Spatiale Toulousaine<br>de Recherche Etudiante</strong>
      </h1>
      <h3 class="text-white smaller">
        L'ASTRE est une association 100% étudiante regroupant des étudiants de l'INSA,<br>ENSEEIHT, ENAC, Université Paul Sabatier et ISAE-SUPAERO.
      </h3>
    </div>
  </div>

  <div bind:this={video} class="video-wrapper">
    <video
      src="https://d1c96hlcey6qkb.cloudfront.net/d075a1d3-d247-4d3d-82f6-aee8f799e7a5/75d979e30ac14b5b9f2d6522dbf78284.preview.mp4?response-content-type=video%2Fmp4&Expires=1718755200&Signature=R4tqpflBtBh8pUk9xqFt56w4o7YzOyPJQNEvAVYon5DaPgGAZC4jlO1eOxmmlnRfkoWYdG2Ed2ICEKyK6SBGtEBJPe1OMhg3yumhtVJFcbgCmdZOVFvrLozKSLRP5OuHo5CLCNpTmn-3LRk~3c2QpuD1GG2jNrnOyCCTYlDRyUX7WksADSYCi2esqzDjvPVM4K9RhQOzb3uHsB6xj7r37v8qAXYxtFCLAWD~9u~L8G6dHM0kS4albxnGvrEv70GZd8F4TWTBnz7VKKUsWXkWSeOjcTeS5QvntZ7byWNgIV4cdOvcmo-ic08AmTyK~3JkbBbPMMlEFiE-QEi6BCcObw__&Key-Pair-Id=APKAI33AGAEAYCXFBDTA"
      autoplay
      loop
      muted
    ></video>
  </div>

  <div class="part-1">
    <h1 class="big-guillemet"><strong>“</strong></h1>
    <h2 class="big-paragraphe">
      Créée le 5 octobre 2017 par douze étudiants de l’<strong>INSA</strong> (Institut National des Sciences Appliquées), l'<strong>ASTRE</strong> est une association étudiante dont l'objectif principal est de constituer une <strong>structure</strong> dans laquelle les étudiants pourront apprendre autour de l’ingénierie spatiale grâce à des projets <strong>techniques</strong> et <strong>concrets</strong>. <br> <br> Le cœur de l’association est alimenté par la réalisation de ses <strong>projets</strong>, nourris par l’expérience et le partage entre les membres qui les composent.
    </h2>
  </div>

  <div class="customers">
    <h1 class="text-black partenaires">Nos partenaires</h1>
    <div class="photobanner">
      <img src="/cnes.png" alt="Logo 1">
      <img src="/csut.png" alt="Logo 2">
      <img src="/enac.png" alt="Logo 3">
      <img src="/n7.png" alt="Logo 4">
      <img src="/sup.png" alt="Logo 5">
      <img src="/ups.png" alt="Logo 6">
      <img src="/cnes.png" alt="Logo 7">
      <img src="/csut.png" alt="Logo 8">
      <img src="/enac.png" alt="Logo 9">
      <img src="/n7.png" alt="Logo 10">
      <img src="/sup.png" alt="Logo 11">
      <img src="/ups.png" alt="Logo 12">
    </div>
  </div>

  <div class="part-2">
    <div class="background-0" bind:this={background0}></div>
    <div class="content projet-1">
      <h1 class="text-white small projet-1">
        <strong>TOLOSAT</strong>
      </h1>
      <h2 class="text-white smaller projet-1">
        TOLOSAT est un projet CubeSat 3U développé conjointement avec le Club<br>CubeSat de l’ISAE-SUPAERO dans lequel 70 étudiants sont répartis en 12<br>équipes de différents domaines d'ingénierie.
      </h2>
      <a href="projets" class="btn btn-primary rounded-pill btn-lg projet-1">
        READ NOW
      </a>
    </div>
  </div>

  <style>
    @font-face {
      font-family: 'Exo2';
      src: url('/fonts/exo2.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }
    @font-face {
      font-family: 'Space';
      src: url('/fonts/quicksand.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }
    @font-face {
      font-family: 'Guillemet';
      src: url('/fonts/gui.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }

    .text-white {
      color: #fff;
    }
    .text-black {
      color: #7d7d7d;
    }
    .big-paragraphe {
      color: #7d7d7d;
      font-size: 1.7rem;
      margin-top: -30px;
    }
    .big-guillemet {
      color: #7d7d7d;
      font-size: 5rem;
      font-family: 'Guillemet', sans-serif;
    }
    .small {
      font-size: 3rem;
    }
    .smaller {
      font-size: 1rem;
    }
    .projet-1 {
      position: relative;
      left: 20%;
    }
    .part-0 {
      position: relative;
      background-image: url('/background0.jpg');
      background-repeat: repeat;
      background-position: center;
      background-size: cover;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 120vh;
      margin-top: -100px;
      padding-top: 0px;
      z-index: 0;
      font-family: 'Exo2', sans-serif;
    }
    .part-1 {
      height: 100vh;
      margin-top: -270px;
      padding-top: 0px;
      padding: 450px;
      justify-content: center;
      font-family: 'Space', sans-serif;
    }
    .customers {
      margin-top: -70px;
      height: 220px;
      position: relative;
      overflow: hidden;
      background-color: #f0f0f0;
      text-align: center;
      padding: 20px 0;
    }
    .partenaires {
      margin-top: 15px;
      font-size: 1rem;
    }
    .photobanner {
      display: inline-block;
      margin-top: 10px;
      white-space: nowrap;
      animation: bannermove 40s linear infinite;
    }
    .photobanner img {
      height: 90px;
      margin: 0 60px;
      vertical-align: middle;
    }
    @keyframes bannermove {
      0% {
        transform: translate(0, 0);
      }
      100% {
        transform: translate(-50%, 0);
      }
    }
    .part-2 {
      position: relative;
      background-image: url('/bg.jpg');
      background-repeat: no-repeat;
      background-position: center;
      background-size: cover;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin-top: 0px;
      padding-top: 0px;
      z-index: 0;
    }
    .content {
      position: relative;
      text-align: center;
      padding: 20px;
      z-index: 3;
    }
    .content.projet-1 {
      text-align: left;
      left: 20%;
    }
    .background-0 {
      background-image: url('/earth.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      width: 40%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 10;
      z-index: 2;
    }
    .video-wrapper {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 0px;
      will-change: transform;
      z-index: 4;
    }
    video {
      max-width: 52%;
      height: auto;
      border-radius: 15px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
  </style>
</main>
