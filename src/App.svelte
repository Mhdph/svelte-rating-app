<script lang="ts">
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";

  let Feedback = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 2,
      rating: 9,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
    {
      id: 3,
      rating: 8,
      text: "Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.",
    },
  ];

  $: count = Feedback.length;
  $: avarage =
    Feedback.reduce((a, { rating }) => a + rating, 0) / Feedback.length;

  const deleteFeedback = (e) => {
    const itemId = e.detail;
    Feedback = Feedback.filter((item) => item.id != itemId);
  };
</script>

<main class="container">
  <FeedbackStats {count} average={avarage} />
  <FeedbackList feedback={Feedback} on:delete-feedback={deleteFeedback} />
</main>
