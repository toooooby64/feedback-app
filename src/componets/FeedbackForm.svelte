<script>
  import Button from "./Button.svelte";
  import Card from "./Card.svelte";
  import RatingButton from "./RatingButton.svelte";
  import { createEventDispatcher } from "svelte";
  let text = "";
  let btnDisabled = true;
  let rating = 10;
  const minMessageLength = 10;
  let message;
  const dispatch = createEventDispatcher();
  const handleInput = () => {
    if (text.trim().length <= minMessageLength) {
      message = `Text must be at least ${minMessageLength} characters long`;
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  const handleSelect = (e) => {
    rating = e.detail;
  };

  const handleSubmit = (e) => {
    const newFeedback = {
      id: Math.floor(Math.random() * 1000),
      rating: +rating,
      text,
    };
    dispatch("handleSubmit", newFeedback);
  };
</script>

<Card>
  <header>
    <h2>How would you rate your experience with us?</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <RatingButton selected={rating} on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        on:input={handleInput}
        placeholder="Tell us about your experience!"
      />
      <Button disabled={btnDisabled} type="submit">Send</Button>
    </div>
    {#if message}
      <div class="message">
        {message}
      </div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
