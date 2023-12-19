<script>
  import { handle_promise } from "svelte/internal";
  import FeedbackItem from "./FeedbackItem.svelte";
  import Stats from "./Stats.svelte";
  export let feedback = [];
</script>

<Stats {feedback} on:handleInput />
{#each feedback as item (item.id)}
  <FeedbackItem {item} on:delete-feedback />
{/each}
