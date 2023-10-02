<script>
  export let onClick = () => {};
</script>

<button on:click={onClick}>
  <label for="profile" tabindex="-1" class="btn btn-ghost btn-circle avatar">
    <div class="w-10 rounded-full">
      <img src="profile.png" alt="Profile" id="profile" />
    </div>
  </label>
</button>
