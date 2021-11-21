<script lang="ts">
  import type { Category } from "./types";
  import VoteCard from "./VoteCard.svelte";
  import CategoryProposal from "./CategoryProposal.svelte";
  import Modal from "./Modal.svelte";
  import CategoryVoteItem from "./CategoryVoteItem.svelte";
  import Header from "./Header.svelte";

  let categories: Category[] = [
    {
      id: "cat-0",
      title: "Test title 1",
      description:
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce elementum, ex et ultrices rhoncus, nisi urna pretium erat, vel consectetur turpis lacus sed velit. Morbi a aliquam libero.",
    },
    {
      id: "cat-1",
      title: "Test title 2",
      description: "Test description",
    },
    {
      id: "cat-2",
      title: "Test title 3",
      description: "Test description",
    },
  ];

  let votes: Map<string, number> = new Map();
  let isModalOpen = false;

  enum Phase {
    PROPOSALS,
    CATEGORY_VOTING,
    VOTING,
    RESULTS,
  }

  let phase: Phase = Phase.PROPOSALS;
</script>

<svelte:head>
  <title>Τα ακάμπανα βραβεία 2021</title>
</svelte:head>

<Header name="George" logout={() => {}} />
<main>
  <div class="w3-row">
    <div class="w3-col s6">
      <div
        class="primary"
        style="margin:auto; font-size: 48pt; vertical-align: top;"
      >
        2021
      </div>
    </div>
    <div class="w3-col s6" style="padding-top: 20px;">
      <div
        class="primary"
        style="text-align: left; font-size: 16pt; vertical-align: top;"
      >
        ΤΑ ΑΚΑΜΠΑΝΑ
      </div>
      <div class="secondary" style="text-align: left; font-size: 16pt;">
        ΒΡΑΒΕΙΑ
      </div>
    </div>
  </div>

  <!-- Audio -->
  <!-- <audio id="audio" autoplay loop>
    <source src="audio/lounge.mp3" type="audio/mpeg" />
    Your browser does not support the audio tag.
  </audio> -->

  <Modal category={categories[0]} bind:open={isModalOpen} />
  <!-- <button
    on:click={() => {
      isModalOpen = true;
    }}
  >
    Open modal
  </button> -->
  <!-- <div>Phase {phase}</div> -->
  <!-- <button on:click={nextPhase}>Next phase</button> -->

  {#if phase == Phase.PROPOSALS}
    <h2>Προτείνετε κατηγορία</h2>
    <CategoryProposal />
  {:else if phase == Phase.CATEGORY_VOTING}
    <h2>Category Voting</h2>
    {#each categories as cat (cat.id)}
      <CategoryVoteItem category={cat} bind:voteValue={votes[cat.id]} />
    {/each}
  {:else if phase == Phase.VOTING}
    <h2>Voting</h2>
    {#each categories as cat (cat.id)}
      <VoteCard category={cat} />
    {/each}
  {:else}
    <h2>Results</h2>
  {/if}
</main>

<style>
  main {
    background-color: #121212;
    color: white;
    text-align: center;
    max-width: 600px;
    margin: 0 auto;
  }

  h2 {
    font: 2.5em Helvetica;
    color: #a9a8a9;
  }
</style>
