<script>
  import Navbar from '$lib/componenets/Navbar.svelte';
  import UserView from '$lib/views/UserView.svelte';
  import LoginView from '$lib/views/LoginView.svelte';
    import { currentUser } from '$lib/pocketbase';
</script>

{#if $currentUser}
  <div class="h-full flex flex-col box-border">
    <Navbar />
    <UserView />
  </div>
{:else}
  <div class="h-full flex flex-col box-border">
    <LoginView />
  </div>
{/if}
