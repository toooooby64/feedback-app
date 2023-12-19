<script>
    export let feedback;

    $: totalFeedback = feedback.length;  
    $: avgRating = () => {
        let sum = 0;
        feedback.forEach(item =>{
            sum += item.rating;
        });
        return (sum / feedback.length).toFixed(1);
    }


</script>

<div class = "stat-container">
    <div class = "total-feedback">
        {totalFeedback} Reviews
    </div>
    <div class = "avg-rating">
        {#if isNaN(avgRating())}
            No ratings yet
        {:else}
            Average Rating: {avgRating()}
        {/if}
        
    </div>
</div>


<style>
    .stat-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 20px 0;
    }
    .avg-rating {
        color: #ff6a95;
        position: relative;
    }
    .total-feedback {
        font-size: 16px;
        color: #aaa;
        position: relative;
        right : -5px;
    }
 
</style>