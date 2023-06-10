<template>
<div v-if="score <= 250">
    <p>OMG! You are god of catching</p>
</div>
<div v-else-if="score > 250 && score < 500">
    <p>You can catch within normal speed</p>
</div>
<div v-else>
    <p>Slow Man.Please try again</p>
</div>
<div>
    <p>Your score was {{score}}ms.</p>
</div>    
</template>

<script>
export default {
    props:['score']
}
</script>

<style>

</style>