<script lang="ts">
  import type { Category } from "./types";

  export let category: Category;
  let selected = "";

  let candidates = [
    { id: "alex", name: "Alex", imageUrl: "images/alex.jpg" },
    { id: "george", name: "George", imageUrl: "images/george.jpg" },
    { id: "helen", name: "Helen", imageUrl: "images/helen.jpg" },
    { id: "john", name: "John", imageUrl: "images/john.jpg" },
    { id: "bill", name: "Bill", imageUrl: "images/bill.jpg" },
  ];

  function auto_grow(event) {
    const element = event.target;
    element.style.height = "5px";
    element.style.height = element.scrollHeight + "px";
  }

  function selectVote(candidateID) {
    return (event) => {
      event.stopPropagation();
      // if (getUserIDFromEmail(firebase.auth().currentUser.email) == candidate)
      //   return;
      selected = candidateID;
    };
  }
</script>

<div class="surface card">
  <div class="w3-row">
    <div class="w3-col s6 w3-padding">
      <h3>{category.title}</h3>
    </div>
    <div class="w3-col s6 w3-padding" style="text-align: left;">
      <p>{category.description}</p>
    </div>
  </div>
  {#each candidates as c (c.id)}
    <img
      src={c.imageUrl}
      class="small selectable {selected == c.id ? 'selected' : ''}"
      on:click={selectVote(c.id)}
      alt={c.name}
    />
  {/each}
  <div style="padding:16px;">
    <textarea
      name="comment"
      class="comment-box"
      placeholder="'ξηγήσου..."
      rows="1"
      on:input={auto_grow}
    />
  </div>
</div>
