<script lang="ts">
  import type { Category } from "./types";

  export let category: Category;
  export let open;

  // When the user clicks on <span> (x), close the modal
  function closeModal(event) {
    if (event.target == this) open = false;
  }
</script>

<div
  on:click={closeModal}
  id="details-modal"
  class="modal {open ? '-open' : ''}"
>
  <!-- Modal content -->
  <div class="modal-content">
    <span class="close" on:click|preventDefault={closeModal}>&times;</span>
    <h3 id="modal-title">{category.title}</h3>
    <p id="modal-details">{category.description}</p>
  </div>
</div>

<style>
  .modal.-open {
    display: block;
  }
</style>
