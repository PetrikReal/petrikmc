<script>
  import Navbar from '$lib/componenets/Navbar.svelte';
  import { currentUser } from '$lib/pocketbase';
  import LoginView from '$lib/views/LoginView.svelte';
</script>

{#if $currentUser}
  <div class="h-full flex flex-col box-border">
    <Navbar />
    <main class="h-full m-2 rounded-xl shadow-2xl p-2 bg-stone-900 box-border">
      <h1 class="text-center font-black p-4 text-4xl">Profil</h1>
      <h1 class="text-center font-bold text-2xl">Felhasználónév: {$currentUser.username}</h1>
      <h1 class="text-center font-bold text-2xl">Bányászérme: {$currentUser.be}</h1>
    </main>
  </div>
{:else}
  <LoginView />
{/if}
