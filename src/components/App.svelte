<div class="w-full h-screen">
  <main class="w-full h-full">
    <div class="input w-1/3 h-20 bg-gray-200 border border-gray-500 rounded relative">
      <input
        type="text"
        bind:value={color}
        placeholder="#d26"
        aria-label="CSS hex value"
        class="w-full mx-auto h-10 text-center text-xl rounded"
        autofocus
      />
      <p class="w-full h-10 text-center text-xl rounded align-center">{rgb}</p>
    </div>
  </main>
  <footer class="absolute w-full bottom-0 p-10">
    <div class="w-1/3 mx-auto">
      <a href="https://github.com/voldemortensen/css-hex-translator">
        <img src="{GitHubPNG}" alt="GitHub.com logo" class="mx-auto" />
      </a>
    </div>
  </footer>
</div>

<style>
  .input {
    top: calc(50% - 2.5rem);
    left: calc(50% - 33.333333% / 2);
  }
</style>

<script>
  import { onMount } from 'svelte';
  import GitHubPNG from '../images/gh-64px.png';

  let color = '';
  let rgb = '';

  $: if (color) {
    let coloredBackground = document.querySelector('.w-full.h-screen');
    let hexRegex = /^#?([a-f0-9]{3,4}|[a-f0-9]{6}|[a-f0-9]{8})$/i;
    if (hexRegex.test(color)) {
      if (!color.startsWith('#')) {
        color = '#' + color;
      }

      coloredBackground.style.background = color;
      rgb = getComputedStyle(coloredBackground).backgroundColor;
    }
  }

  onMount(() => {
    color = '#d26';
  });
</script>
