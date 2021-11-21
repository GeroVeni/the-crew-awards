<script lang="ts">
  export let name;
  export let logout;
</script>

<div class="w3-bar surface">
  <span class="w3-bar-item" id="header-greeting">How you doin', {name}!</span>
  <button class="w3-bar-item w3-button w3-right" on:click={logout}>
    <i class="fas fa-sign-in-alt" />
  </button>
</div>
