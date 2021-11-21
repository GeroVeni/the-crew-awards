<script lang="ts">
  function onSubmit(e: Event) {
    proposalState = 0;
  }

  function auto_grow(event) {
    const element = event.target;
    element.style.height = "5px";
    element.style.height = element.scrollHeight + "px";
  }

  let proposalState = 1;
</script>

{#if proposalState}
  <form on:submit|preventDefault={onSubmit}>
    <input
      type="text"
      name="title"
      placeholder="Τίτλος"
      class="comment-box"
      style="display: inline-block; width: 92%"
    />
    <div class="wrapper">
      <textarea
        name="description"
        id="category-description"
        placeholder="Περιγραφή ..."
        rows="1"
        class="comment-box"
        on:input={auto_grow}
      />
    </div>
    <button style="margin:auto; display:block">Υποβολή</button>
  </form>
{:else}
  <div>
    <div>Your submission for XX was successful!</div>
    <button
      on:click={() => {
        proposalState = 1;
      }}
    >
      Submit another
    </button>
  </div>
{/if}

<style>
  .wrapper {
    margin: 2px 6px;
  }

  .comment-box {
    border-radius: 8px;
    border: 3px solid #bf9b5f;
    background-color: black;
    font-weight: bold;
    padding: 2px 6px;
    width: 95%;
    color: white;
    resize: vertical;

    /* box-sizing: padding-box; */
    overflow: hidden;
  }
</style>
