<script>
  import { getContext } from "svelte";
  import Fiche from "./Fiche.svelte";
  import Counter from "./lib/Counter.svelte";
  import Decounter from "./lib/Decounter.svelte";

  let logo = "logo de svelte";
  let taille = 200;
  let url = "https://www.google.com";
  let urlImg1 =
    "https://images.unsplash.com/photo-1683802175943-c71b4bd66c54?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2286&q=80";
  let urlImg2 =
    "https://images.unsplash.com/photo-1682685797208-c741d58c2eff?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=2370&q=80";
  let src = urlImg1;
  let lien = "Google";
  let compteur = 0;
  let cont = -2;
  function incrementer(e, step = 1) {
    compteur += step;
  }
  function changeImg() {
    src = src === urlImg1 ? urlImg2 : urlImg1;
  }
  let texte = "un beau texte à inverser";
  function inverser() {
    texte = texte.split("").reverse().join("");
  }

  $: prenomV = prenom.toUpperCase();
  function changePrenom() {
    prenom = prenom === "Gonzague" ? "Dominique" : "Gonzague";
  }
  let prenom = "",
    nom = "",
    age = "";
</script>

<main>
  <h1>Mes essais</h1>
  <div class="card">
    <Counter /><Decounter />
  </div>
  <hr />
  <div class="container">
    <h1><a href={url} target="-blank">{lien} et {prenomV.toLowerCase()}</a></h1>
    <button on:click={(e) => incrementer(e, cont)}
      >Par {cont} = {compteur}</button
    >
    <img {src} alt={logo} width={taille} on:click={changeImg} />
  </div>
  <hr />
  <p class="texte"><button on:click={inverser}>Inverser</button>{texte}</p>
  <h1 on:click={changePrenom}>{prenomV}</h1>
  <input type="text" placeholder="Prenom ?" id="prenom" bind:value={prenom} />
  <input type="text" placeholder="Nom ?" id="nom" bind:value={nom} />
  <input type="number" placeholder="Age ?" id="age" bind:value={age} />

  <Fiche {nom} {prenomV} {age} />
  <p>
    Check out <a
      href="https://github.com/sveltejs/kit#readme"
      target="_blank"
      rel="noreferrer">SvelteKit</a
    >, the official Svelte app framework powered by Vite!
  </p>
</main>

<style>
  .container {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }
  img {
    height: auto;
  }
  .texte {
    color: yellow;
    font-size: 2rem;
  }
  h1:hover {
    cursor: pointer;
    color: red;
  }
</style>
