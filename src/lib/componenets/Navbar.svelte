<script lang="ts">
  import { onMount } from 'svelte';
  import UserMenu from './UserMenu.svelte';
  import Icon from '@iconify/svelte';
  import { slide } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';
  import { pb } from '$lib/pocketbase';

  let menuVisible = false;

  function toggleMenu() {
    menuVisible = !menuVisible;
  }

  onMount(() => {
    function handleClickOutside(event: any) {
      const menu = document.getElementById('menu');
      if (menu && !menu.contains(event.target)) {
        menuVisible = false;
      }
    }

    document.addEventListener('mousedown', handleClickOutside);
    return () => {
      document.removeEventListener('mousedown', handleClickOutside);
    };
  });
</script>

<div
  class="bg-stone-900 flex items-center p-1 justify-between mx-2 mt-2 rounded-xl box-border w-auto"
>
  <a class="flex items-center hover:text-emerald-800 transition" href="/">
    <Icon class="text-3xl mx-2" icon="iconamoon:home-bold" />
    <p class="text-xl font-bold mr-2">PetrikMC</p>
  </a>
  <div class="flex flex-row items-center">
    {#if menuVisible}
      <div
        class="flex flex-row"
        transition:slide={{ delay: 250, duration: 300, easing: quintOut, axis: 'y' }}
      >
        <a href="/profile" class="block px-4 py-2 hover:text-emerald-800 transition">Profil</a>
        <a href="/shop" class="block px-4 py-2 hover:text-emerald-800 transition">Shop</a>
        <a
          on:click={() => {
            if (menuVisible) {
              pb.authStore.clear();
            }
          }}
          href="/"
          class="block px-4 py-2 hover:text-emerald-800 transition">Kijelentkezés</a
        >
      </div>
    {/if}
    <UserMenu onClick={toggleMenu} />
  </div>
</div>
