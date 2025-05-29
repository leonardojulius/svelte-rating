<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'

  let firstName = 'Julius';
  let lastName ='Leonardo';
  let color = 'blue';
  let showText = false;

  //Reactive Value;
  $: name = firstName + ' ' + lastName;

  const toggle = () => {
    color = color === 'blue' ? 'red' : 'blue';
    showText = !showText;
  }
</script>

<main>
  <div>
    <a href="https://vite.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>
  <h1 style="color: {color};">{name}</h1>

  {#if showText}
  
    <div class="card">
      <Counter />
    </div>
    <p>
      Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the official Svelte app framework powered by Vite!
    </p>
    <p class="read-the-docs">
      Click on the Vite and Svelte logos to learn more
    </p>
  {:else}
    <p>No Text</p>
  {/if}

  <button on:click={toggle}>Click</button>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
