<script>
  import { onMount } from "svelte";

  export let words = [];
  let displayedText = "";
  let wordIndex = 0;
  let blinkState = false;

  export let delay = 2000;
  export let typingSpeed = 100;
  export let deletingSpeed = 50;

  function sleep(ms) {
    return new Promise((resolve) => setTimeout(resolve, ms));
  }

  const typeCharacter = async (currentWord) => {
    let entries = Array.from(currentWord).entries();

    for (let [index] of entries) {
      displayedText = currentWord.substring(0, index++);
      await sleep(typingSpeed);
    }
  };

  const deleteCharacter = async (currentWord) => {
    for (let i = currentWord.length; i > 0; i--) {
      displayedText = currentWord.substring(0, i - 1);
      await sleep(deletingSpeed);
    }
  };

  async function typeWriterEffect() {
    while (true) {
      const currentWord = words[wordIndex];

      blinkState = true;
      await typeCharacter(currentWord).then(() => (blinkState = false));

      await sleep(delay);

      blinkState = true;
      await deleteCharacter(currentWord).then(() => (blinkState = false));

      await sleep(delay);

      if (wordIndex === words.length - 1) {
        wordIndex = 0;
      } else {
        wordIndex++;
      }
    }
  }

  $: style = `animation-name:${blinkState ? "blink" : ""}`;

  onMount(async () => {
    typeWriterEffect();
  });
</script>

<div>
  <p>{displayedText}</p>
  <span {style}>|</span>
</div>

<style>
  div {
    display: inline;
  }
  p {
    display: inline;
  }
  span {
    caret-shape: block;
    background-color: black;
    width: 20px;
    height: 20px;
    animation: blink 0.5s infinite;
  }

  @keyframes blink {
    50% {
      opacity: 0;
    }
  }
</style>
