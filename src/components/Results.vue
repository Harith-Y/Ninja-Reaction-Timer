<template>
    <div class="results-container">
        <h1>Results</h1>
        <p class="score">Reaction Time: {{ score }} ms</p>
        <p class="rank">Rank: {{ rank }}</p>
        </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 200) {
            this.rank = "Ninja"
        } 
        else if (this.score < 300) {
            this.rank = "Samurai"
        } 
        else if (this.score < 400) {
            this.rank = "Warrior"
        } 
        else {
            this.rank = "Beginner"
        }   
    },
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
    .results-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 20px;
        background-color: #577d53;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        margin: 20px;
    }

    .score {
        font-size: 2em;
        color: #333;
        margin-bottom: 10px;
    }

</style>