<script lang="ts">
  import { onMount } from "svelte";
  export let words = [];

  let index = 0;
  let output = "";
  setInterval(() => {
    output = `${words[index]}`;
    index = index + 1;
    if (index == words.length) index = 0;
  }, 5000);

  onMount(() => {
    setInterval(() => {
      output = `${words[index]}`;
      index = index + 1;
      if (index == words.length) index = 0;
    }, 5000);
  });
</script>

<div>
  <h1>{output}</h1>
</div>

<style>
  div {
    overflow: hidden;
    font-size: 20px;
    min-width: 3rem;
    width: 100%;
    border: 1px solid red;
  }
  h1 {
    display: block;
    position: relative;
    overflow: hidden;
    animation: rotate_word_animation;
    animation-duration: 5s;
    animation-iteration-count: infinite;
  }

  @keyframes rotate_word_animation {
    0% {
      transform: translate3d(0, -80px, 0);
      opacity: 0;
    }
    20%,
    80% {
      transform: translate3d(0, 0, 0);
      opacity: 1;
    }
    100% {
      transform: translate3d(0, 40px, 0);
      opacity: 0;
    }
  }
</style>
