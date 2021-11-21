<script lang="ts">
  import type { Category } from "./types";

  export let category: Category;
  export let voteValue: number;
</script>

<div class="w3-row">
  <div class="w3-col s6">
    <div>
      <b>{category.title}</b>
      <span class="info-icon">i</span>
    </div>
  </div>
  <div class="w3-col s6">
    <label class="container -no {voteValue == -1 ? 'selected' : ''}">
      <span>-1</span>
      <input type="radio" bind:group={voteValue} name="vote" value={-1} />
    </label>
    <label class="container -zero {voteValue == 0 ? 'selected' : ''}">
      <span>0</span>
      <input type="radio" bind:group={voteValue} name="vote" value={0} />
    </label>
    <label class="container -yes {voteValue == +1 ? 'selected' : ''}">
      <span>+1</span>
      <input type="radio" bind:group={voteValue} name="vote" value={+1} />
    </label>
  </div>
</div>

<style>
  .info-icon {
    display: inline-block;
    height: 1.5em;
    width: 1.5em;
    border: 1px solid white;
    border-radius: 50%;
  }

  /* The container */
  .container {
    display: inline-block;
    position: relative;
    margin-bottom: 12px;
    cursor: pointer;
    font-size: 24px;
    width: 1.3em;
    background-color: #242424;
    border-radius: 20%;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .container:hover {
    background-color: #303030;
  }

  /* Hide the browser's default radio button */
  .container input {
    display: none;
    cursor: pointer;
  }

  .container.-no.selected {
    background-color: salmon;
  }
  .container.-zero.selected {
    background-color: khaki;
  }
  .container.-yes.selected {
    background-color: lightgreen;
  }
</style>
