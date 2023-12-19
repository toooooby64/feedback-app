<script>
  import FeedbackForm from "./componets/FeedbackForm.svelte";
  import FeedbackList from "./componets/FeedbackList.svelte";
  import Stats from "./componets/Stats.svelte";
  let feedback = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque nisl eros, pulvinar facilisis justo mollis, auctor consequat urna. Morbi a bibendum metus.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque nisl eros, pulvinar facilisis justo mollis, auctor consequat urna. Morbi a bibendum metus.",
    },
    {
      id: 3,
      rating: 3,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque nisl eros, pulvinar facilisis justo mollis, auctor consequat urna. Morbi a bibendum metus.",
    },
    {
      id: 4,
      rating: 7,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque nisl eros, pulvinar facilisis justo mollis, auctor consequat urna. Morbi a bibendum metus.",
    },
    {
      id: 5,
      rating: 4,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque nisl eros, pulvinar facilisis justo mollis, auctor consequat urna. Morbi a bibendum metus.",
    },
  ];

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    feedback = feedback.filter((item) => item.id !== itemId);
  };
  const handleSubmit = (e) => {
    const newFeedback = e.detail;
    feedback = [newFeedback, ...feedback];
  };

</script>

<main class = "container">
  <FeedbackForm on:handleSubmit={handleSubmit}/>
  <FeedbackList {feedback} on:delete-feedback = {deleteFeedback} onL/>
</main>
