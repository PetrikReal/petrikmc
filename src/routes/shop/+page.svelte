<script>
  import Navbar from '$lib/componenets/Navbar.svelte';
  import { currentUser } from '$lib/pocketbase';
  import LoginView from '$lib/views/LoginView.svelte';
  import ProductCard from '$lib/componenets/ProductCard.svelte';

  
</script>

{#if $currentUser}
  <div class="h-full flex flex-col box-border">
    <Navbar />
    <main class="h-full m-2 rounded-xl shadow-2xl p-2 bg-stone-900 box-border">
      <h1 class="text-center font-black p-4 text-4xl">Bolt</h1>
      <ProductCard />
    </main>
  </div>
{:else}
  <LoginView />
{/if}
