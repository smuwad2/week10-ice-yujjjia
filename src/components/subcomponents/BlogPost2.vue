<script>
export default {
    // Add code if/as necessary
    // Hint: Add properties subject, entry and mood
    props: {
        subject: String,    // expects text
        entry: String,      // expects text
        mood: String        // expects text like "happy", "sad", "angry"
    },
    computed: {
        imgLoc() {
            return `/assets/${this.mood.toLowerCase()}.png`
        }
    }
}
</script>


<template>
    <!-- TODO: add your template code here. Use bootstrap card -->
    <div class="card" style="width: 18rem;">
        <img :src="imgLoc" class="card-img-top" alt="...">
        <div class="card-body">
            <h5 class="card-title">{{subject}}</h5>
            <p class="card-text">{{entry}}</p>
        </div>
        <slot></slot>
    </div>

</template>
