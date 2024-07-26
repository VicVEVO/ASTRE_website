<script>
  import Navbar from "../widget/Navbar.svelte";
  import { onMount } from 'svelte';

  let video, logo_img, rocket_img, satellite_img, balloon_img;
  let y = 0;
  let opacity_video = 0;
  
	$: {
	  if (y < 50) {
      opacity_video = 0;
	  } else if (y < 400) {
      opacity_video = (y - 50) / 100;
	  } else {
      opacity_video = 1;
	  }
	}
  const handleScroll = () => {
  const scrollPosition = window.scrollY;
  const parallaxSpeed = -0.1;

  function easeOutCirc(x) {
      return Math.sqrt(1 - Math.pow(x - 1, 2));
  }
  const easedScrollPosition = easeOutCirc(scrollPosition/window.innerHeight);

  video.style.transform = `translateY(${scrollPosition * parallaxSpeed}px)`;
  logo_img.style.transform = `translateY(${scrollPosition * parallaxSpeed / 2}px)`;
  satellite_img.style.transform = `rotate(${scrollPosition * parallaxSpeed / 20}deg)`;
  balloon_img.style.transform = `translateY(${scrollPosition * parallaxSpeed}px)`;
  rocket_img.style.transform = `translateX(${1000000000*easedScrollPosition}px)`;
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
  <div class="welcome">
    <div class="big-logo" bind:this={logo_img}></div>
    <div class="content">
      <h1 class="text-white small">
        <strong>Association Spatiale Toulousaine<br>de Recherche Etudiante</strong>
      </h1>
      <h3 class="text-white smaller">
        L'ASTRE est une association 100% étudiante regroupant des étudiants de l'INSA,<br>ENSEEIHT, ENAC, Université Paul Sabatier et ISAE-SUPAERO.
      </h3>
    </div>
  </div>

  <div bind:this={video} class="video-wrapper" style="opacity: {opacity_video};">
    <video
      src="https://sscspace.canto.global/direct/video/encnjooao55ln7pdckhdnts244/Jh39kf6rhvM2ID6rPWTTkfNS6yw/play"
      autoplay
      loop
      muted
    ></video>
  </div>

  <div class="sum-up">
    <h1 class="big-guillemet"><strong>“</strong></h1>
    <h2 class="big-paragraphe">
      Créée le 5 octobre 2017 par douze étudiants de l’<strong>INSA</strong> (Institut National des Sciences Appliquées), l'<strong>ASTRE</strong> est une association étudiante dont l'objectif principal est de constituer une <strong>structure</strong> dans laquelle les étudiants pourront apprendre autour de l’ingénierie spatiale grâce à des projets <strong>techniques</strong> et <strong>concrets</strong>. <br> <br> Le cœur de l’association est alimenté par la réalisation de ses <strong>projets</strong>, nourris par l’expérience et le partage entre les membres qui les composent.
    </h2>
  </div>

  <div class="customers">
    <h1 class="text-black partenaires">Nos partenaires</h1>
    <div class="photobanner">
      <img src="/partenaires/cnes.png" alt="Logo 1">
      <img src="/partenaires/csut.png" alt="Logo 2">
      <img src="/partenaires/enac.png" alt="Logo 3">
      <img src="/partenaires/n7.png" alt="Logo 4">
      <img src="/partenaires/sup.png" alt="Logo 5">
      <img src="/partenaires/ups.png" alt="Logo 6">
      <img src="/partenaires/cnes.png" alt="Logo 7">
      <img src="/partenaires/csut.png" alt="Logo 8">
      <img src="/partenaires/enac.png" alt="Logo 9">
      <img src="/partenaires/n7.png" alt="Logo 10">
      <img src="/partenaires/sup.png" alt="Logo 11">
      <img src="/partenaires/ups.png" alt="Logo 12">
    </div>
  </div>

  <div class="projects">
    <div class="img-satellite" bind:this={satellite_img}></div>
    <div class="content projet-1">
      <h1 class="text-white small projet-1">
        <strong>TOLOSAT</strong>
      </h1>
      <h2 class="text-white smaller projet-1">
        TOLOSAT est un projet CubeSat 3U développé conjointement avec le Club<br>CubeSat de l’ISAE-SUPAERO dans lequel 70 étudiants sont répartis en 12<br>équipes de différents domaines d'ingénierie.
      </h2>
      <a href="./projets" class="btn btn-primary rounded-pill btn-lg projet-1 btn-custom">
        Lire la suite
      </a>
    </div>

    <div class="img-balloon" bind:this={balloon_img}></div>
    <div class="content projet-2">
      <h1 class="text-white small projet-2">
        <strong>ASTRE'LOON</strong>
      </h1>
      <h2 class="text-white smaller projet-2">
        ASTRE'LOON est le projet de ballon sonde de l'ASTRE. Ce dernier participe à <br> la campagne annuelle de lancement C'Space organisée par le CNES.      </h2>
      <a href="projets" class="btn btn-primary rounded-pill btn-lg projet-2 btn-custom">
        Lire la suite
      </a>
    </div>
    <div class="img-rocket" bind:this={rocket_img}></div>
    <div class="content projet-3">
      <h1 class="text-white small projet-3">
        <strong>ASTRE'LAUNCH</strong>
      </h1>
      <h2 class="text-white smaller projet-3">
        ASTRE'LAUNCH est le programme de fusées expérimentales de l'ASTRE. 
      </h2>
      <a href="projets" class="btn btn-primary rounded-pill btn-lg projet-3 btn-custom">
        Lire la suite
      </a>
    </div>
  </div>

  <div class="contacts">
    <h1 class="text-white partenaires">Nous contacter</h1>
  </div>

  <style>
    /* Fonts */
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
    /* Text custom settings */
    .text-white {
      color: #fff;
    }
    .text-black {
      color: #7d7d7d;
    }
    .small {
      font-size: calc(1.5rem + 1.5vw);;
    }
    .smaller {
      font-size: calc(0.75rem + 0.25vw);
    }
    .big-paragraphe {
      color: #7d7d7d;
      font-size: calc(1rem + 0.55vw);
      margin-top: -1rem;
      text-align: justify;
    }
    .big-guillemet {
      color: #7d7d7d;
      font-size: 5rem;
      font-family: 'Guillemet', sans-serif;
    }
    /* Button settings */
    .btn-custom {
      background-color: #6b5119;
      border: 0.15rem solid transparent;
      color: #fff;
      position: relative;
      overflow: hidden;
      z-index: 1;
      transition: background-color 0.4s, color 0.4s;
    }
    .btn-custom::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: #fff;
      z-index: -1;
      transition: transform 0.4s;
      transform: scaleX(0);
      transform-origin: right;
    }
    .btn-custom:hover::before {
      transform: scaleX(1);
      transform-origin: left;
    }
    .btn-custom:hover {
      background-color: #967329;
      color: #6b5119;
      border-color: #967329;
      text-shadow: 0rem .1rem .2rem rgb(255, 255, 255);
    }
    .projet-2.btn-custom {
      background-color: #2e507e;
    }
    .projet-2.btn-custom:hover {
      background-color: #5181c4;
      color: #2e507e;
      border-color: #5181c4;
    }
    .projet-3.btn-custom {
      background-color: #222222;
    }
    .projet-3.btn-custom:hover {
      background-color: #3a3a3a;
      color: #222222;
      border-color: #3a3a3a;
    }
    /* Images */
    .big-logo {
      background-image: url('/logo2.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      width: 40%;
      height: 100%;
      position: absolute;
      z-index: 2;
    }
    .img-rocket {
      background-image: url('/rocket.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      width: 100%;
      height: 50%;
      position: absolute;
      top: 60%;
      left: -00%;
      z-index: 2;
    }
    .img-satellite {
      background-image: url('/satellite.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      width: 35%;
      height: 25%;
      position: absolute;
      top: 10%;
      left: 12%;
      z-index: 2;
    }
    .img-balloon {
      background-image: url('/ballon.png');
      background-repeat: no-repeat;
      background-position: center;
      background-size: contain;
      width: 15%;
      height: 80%;
      position: absolute;
      top: 20%;
      left: 65%;
      z-index: 2;
    }
    /* Video */
    .video-wrapper {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 0rem;
      will-change: transform;
      z-index: 4;
    }
    video {
      max-width: 52%;
      height: auto;
      border-radius: 1rem;
      box-shadow: 0 0.3rem 0.5rem rgba(0, 0, 0, 0.2);
    }

    /* Parts of the website */
    .projet-1 {
      position: relative;
      left: 20%;
      top: -17rem;
    }
    .projet-2 {
      position: relative;
      right: 20%;
      top: 0rem;
    }
    .projet-3 {
      position: relative;
      left: 0%;
      top: 15rem;
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
      height: 70rem;
      margin-top: -5rem;
      padding-top: 0rem;
      z-index: 0;
      font-family: 'Exo2', sans-serif;
    }
    .sum-up {
      height: 55rem;
      margin-top: -19rem;
      padding-top: 0rem;
      padding: 30rem;
      justify-content: center;
      font-family: 'Space', sans-serif;
    }
    .projects {
      position: relative;
      background-image: url('/big_bg.png');
      background-repeat: no-repeat;
      background-position: center;
      overflow: hidden;
      background-size: cover;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 150rem;
      margin-top: 0rem;
      padding-top: 0rem;
      z-index: 0;
    }
    .customers {
      margin-top: -3rem;
      height: 15rem;
      position: relative;
      overflow: hidden;
      background-color: #f0f0f0;
      text-align: center;
      padding: 1.5rem 0;
    }
    .contacts {
      margin-top: -2rem;
      height: 10rem;
      position: relative;
      overflow: hidden;
      background-color: #111110;
      text-align: center;
      padding: 2rem 0;
    }
    /* Customers */
    .partenaires {
      margin-top: 1.5rem;
      font-size: 1rem;
    }
    .photobanner {
      display: inline-block;
      margin-top: 1.7rem;
      white-space: nowrap;
      animation: bannermove 40s linear infinite;
    }
    .photobanner img {
      height: 5.6rem;
      margin: 0 3.85rem;
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
    .content {
      position: relative;
      text-align: center;
      z-index: 3;
      text-shadow: 0rem .1rem .2rem rgb(4, 1, 15);
    }    

  /* Styles pour les écrans moyens */
  @media (max-width: 1280px) {
    .welcome {
      height: 60rem;
      margin-top: -5rem;
      padding-top: 0rem;
    }
    .big-logo {
      width: 35rem;
      background-position: center;
      background-size: contain;
      width: 60%;
      height: 100%;
      position: absolute;
    }
    video {
      max-width: 80%;
    }
    .sum-up {
      height: 32rem;
      margin-top: 2rem;
      padding-top: 0rem;
      padding: 5rem;
    }
    .photobanner {
      animation: bannermove 20s linear infinite;
    }
    .projects {
      height: 100rem;
      margin-top: 0rem;
      padding-top: 0rem;
    }
    .content.projet-1 {
      left: -10%;
      top: 0rem;
    }
    .content.projet-2 {
      left: 0%;
      top: 0rem;
    }
    .content.projet-3 {
      left: 3%;
      top: 0rem;
    }
    .img-satellite {
      width: 30rem;
      top: 12%;
      left: 25%;
    }
    .img-balloon {
      width: 10rem;
      top: 25%;
      left: 70%;
    }
    .img-rocket {
      width: 5rem;
      top: 65%;
      left: 10%;
    }
  }

  /* Styles pour les petits écrans */
  @media (max-width: 768px) {
  }

  /* Styles pour les très petits écrans */
  @media (max-width: 480px) {
    .small {
      font-size: calc(1rem + 1.5vw);;
    }
    .smaller {
      font-size: calc(0.5rem + 0.25vw);
    }
    .welcome {
      height: 45rem;
      margin-top: -5rem;
      padding-top: 0rem;
    }
    .big-logo {
      background-position: center;
      background-size: contain;
      width: 80%;
      height: 100%;
      position: absolute;
    }
    video {
      max-width: 90%;
    }
    .sum-up {
      height: 30rem;
      margin-top: 1rem;
      padding-top: 0rem;
      padding: 2rem;
    }
    .customers {
      margin-top: 0rem;
      height: 10rem;
      padding: .5rem 0;
    }
    .photobanner {
      padding: 1.5rem 0;
      margin-top: -0rem;
      animation: bannermove 15s linear infinite;
    }
    .photobanner img {
      height: 3rem;
      margin: 0 2rem;
    }
    .projects {
      height: 80rem;
      margin-top: 0rem;
      padding-top: 0rem;
    }
    .content.projet-1 {
      left: -13%;
      top: 0rem;
    }
    .content.projet-2 {
      left: 7%;
      top: 0rem;
    }
    .content.projet-3 {
      left: -8%;
      top: 0rem;
    }
    .img-satellite {
      width: 30rem;
      top: 8%;
      left: -2%;
    }
    .img-balloon {
      width: 10rem;
      top: 20%;
      left: 62%;
    }
    .img-rocket {
      width: 5rem;
      top: 65%;
      left: 10%;
    }
  }

  </style>

</main>

<svelte:window bind:scrollY={y} />