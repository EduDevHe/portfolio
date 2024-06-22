<script lang="ts">
  import Typewriter from "../animations/Typewriter.svelte";
</script>

<div>
  <article>
    <h1>eduardo dev</h1>
    <div>
      <span>&lt;</span>
      <Typewriter words={["FRONT-END/> ", "BACK-END/> ", "FULL-STACK/>"]} />
    </div>
  </article>
  <section></section>
</div>

<style>
  div {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr;
    gap: 0px 0px;
    grid-auto-flow: row;
    grid-template-areas: "article section";
  }

  article {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    grid-area: article;
    border: 1px solid red;
  }

  article > h1 {
    text-transform: uppercase;
  }

  article > div {
    display: flex;
    flex-direction: row;
    align-items: center;
    min-width: 2.5rem;
    width: 25rem;
    font-size: 2rem;
    font-weight: 700;
    padding: 1rem;
    justify-content: center;
    text-transform: uppercase;
  }

  section {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid blue;
  }
</style>
