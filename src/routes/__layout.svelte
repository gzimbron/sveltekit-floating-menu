<script>
  import { componenteName } from '../config';
</script>

<svelte:head>
  <title>ZimbronApps.com</title>
</svelte:head>

<div class="core-wrapper">
  <header>
    <h1>
      ZimbronApps.com
      <span class="componente">
        {componenteName}
      </span>
    </h1>
    <div class="svelte">SvelteKit</div>
  </header>
  <div class="slot-wrapper">
    <slot />
  </div>
</div>

<style>
  .core-wrapper {
    min-height: 100vh;
    max-height: 100vh;
    display: grid;
    grid-template-rows: auto 1fr;
    overflow-y: hidden;
  }
  header {
    position: relative;
    background: steelblue;
    color: white;
    text-align: center;
    padding: 5vh 20px;
  }
  h1 {
    font-family: 'Yanone Kaffeesatz', sans-serif;
    font-size: 2.5em;
    text-align: 'center';
    margin: 0;
    display: inline-block;
    letter-spacing: 1px;
  }
  h1 .componente {
    color: skyblue;
    font-size: 2rem;
    letter-spacing: 2px;
  }
  .svelte {
    position: absolute;
    bottom: 0;
    right: 0;

    font-size: 1.1rem;
    padding: 2px 5px;
    background: lightblue;
    color: steelblue;
  }

  .slot-wrapper {
    background-color: lightcyan;
    padding: 20px;
    max-height: 100%;
    overflow-y: auto;
  }
</style>
