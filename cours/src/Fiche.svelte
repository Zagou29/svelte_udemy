<script>
  /* reçoit les variables de App */
  export let prenom, nom, age;

  $: annees = age > 1 ? "ans" : age === 1 ? "an" : "";
  $: ageV = age < 1 ? "" : age;
</script>

<div class="fiche">
  <p>nom : {prenom} {nom}</p>
  <p>Age : {ageV} {annees}</p>
</div>

<style>
  .fiche {
    width: 25rem;
    height: 10rem;
    margin: 1rem auto;
    padding: 2rem;
    background: lightgreen;
    font-size: 1.6rem;
    color: black;
    text-align: left;
  }
</style>
