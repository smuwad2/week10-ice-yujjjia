<script>
export default {
    props: {
        subject: String,
        entry: String,
        mood: String
    },
    computed: {
        imgLoc() {
            // Handle undefined/null mood gracefully
            const moodValue = this.mood || 'happy'
            return `/assets/${moodValue.toLowerCase()}.png`
        }
    }
}
</script>

<template>
    <div class="card" style="width: 18rem;">
        <img :src="imgLoc" class="card-img-top" alt="mood icon">
        <div class="card-body">
            <h5 class="card-title">{{ subject }}</h5>
            <p class="card-text">{{ entry }}</p>
        </div>
    </div>
</template>