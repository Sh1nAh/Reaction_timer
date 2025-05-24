<template>
    <p>Reaction time - {{ score }} ms</p>
    <div v-if="score < 500">
        <p class="result">OMG! You are god of catching</p>
    </div>
    <div v-else-if="score > 500 && score < 700">
        <p class="result">Nice catch!</p>
    </div>
    <div v-else>
        <p class="result">Slow man! Catch me fast</p>
    </div>
</template>

<script>
export default {
    props: ['score']
}
</script>

<style>
    p {
        font-size: 14px;
    }
    .result {
        font-size: 16px;
        font-weight: bold;
        color: #7532a2;
    }
</style>