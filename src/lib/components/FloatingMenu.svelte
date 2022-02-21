<script lang="ts">
  import { fly } from 'svelte/transition';
  type FloatingMenuItem = {
    label: string;
    icon: string;
    onClick: () => void;
  };

  export let items: FloatingMenuItem[] = [];
  export let buttonColor: string = 'coral';
  export let hoverColor: string = '#ffc107';
  export let iconHoverColor: string = buttonColor;
  export let itemHoverColor: string = hoverColor;

  export let isOpen = false;

  export let icon: string = 'more_vert';

  const toggleMenu = () => {
    isOpen = !isOpen;
  };
  const elementClick = (callback: () => void) => {
    toggleMenu();
    callback();
  };
</script>

<div
  class="menu-container"
  style:--button-color={buttonColor}
  style:--hover-color={hoverColor}
  style:--icon-hover-color={iconHoverColor}
  style:--item-hover-color={itemHoverColor}
>
  <div class="menu-button" on:click={toggleMenu}>
    <span class="material-icons buttontxt">{icon}</span>
  </div>

  {#if isOpen}
    <div class="items-container" transition:fly>
      {#each items as item}
        <div class="item-container" on:click={() => elementClick(item.onClick)}>
          <span class="material-icons icon">{item.icon}</span>
          <span>{item.label}</span>
        </div>
      {/each}
    </div>
  {/if}
</div>

<style>
  .menu-container {
    position: relative;
    /* prevent selection */
    -webkit-touch-callout: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .menu-button {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    padding: 5px;
    border-radius: 50%;
    cursor: pointer;
    aspect-ratio: 1;
    background: var(--button-color);
    color: white;
    transition: all 0.2s ease-in-out;
  }

  .menu-button:hover {
    background: var(--hover-color);
  }

  .buttontxt {
    font-size: 1.5rem;
  }

  .items-container {
    position: absolute;
    background: white;
    top: 100%;
    margin-top: 5px;
    border-radius: 5px;
    padding: 5px 0;
    box-shadow: 0px 0px 10px 0px rgba(0, 0, 0, 0.1);
    min-width: 100px;
  }

  .item-container {
    position: relative;
    white-space: nowrap;
    display: flex;
    align-items: center;
    font-size: 14px;
    gap: 10px;
    padding: 5px 12px;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
  }

  .item-container:hover {
    background: var(--item-hover-color);
    color: white;
    transform: scale(1.2);
  }

  .icon {
    font-size: 14px;
    transition: all 0.2s ease-in-out;
  }

  .item-container:hover > .icon {
    position: absolute;
    left: 0;
    transform: scale(2) translateX(-100%);
    color: var(--icon-hover-color);
  }
</style>
