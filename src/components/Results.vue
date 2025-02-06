<template>
    <div>
        <h1>Results</h1>
        <p>Reaction Time: {{ score }} ms</p>
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
</style>