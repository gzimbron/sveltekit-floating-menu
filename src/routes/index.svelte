<script lang="ts">
  import FloatingMenu from '$lib/components/FloatingMenu.svelte';

  const menuElements = [
    {
      label: 'Profile',
      icon: 'person',
      onClick: () => {
        area = 'Profile Area';
      },
    },
    {
      label: 'Settings',
      icon: 'settings',
      onClick: () => {
        area = 'Settings Area';
      },
    },
    {
      label: 'Favorites',
      icon: 'favorite',
      onClick: () => {
        area = 'Favorites Area';
      },
    },
  ];

  let area: string = 'Ninguna';

  let isMenu2Open = false;
</script>

<p>Area Actual: {area}</p>
<div class="centrar">
  <FloatingMenu items={menuElements} />
</div>

<div class="spacer" />

<div class="centrar">
  <FloatingMenu
    bind:isOpen={isMenu2Open}
    items={menuElements}
    icon={isMenu2Open ? 'close' : 'menu'}
    buttonColor={isMenu2Open ? '#E21717' : 'steelblue'}
    hoverColor={isMenu2Open ? '#E21717' : 'lightblue'}
    iconHoverColor="#2827CC"
    itemHoverColor="#22CB5C"
  />
</div>

<style>
  .centrar {
    display: flex;
    justify-content: center;
  }
  .spacer {
    height: 150px;
  }
</style>
