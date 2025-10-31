<script>
    export default { 
        data() {
            return {
                soundEmojis: ['🔇', '🔈', '🔉', '🔊']
            }
        },
        // TODO: add code to define a necessary prop
        props: {
            soundLevel: {
                type: Number,
                required: true
            }
        },
        computed: {
            // compute the emoji from the numeric soundLevel
            emoji() {
                const idx = this.soundLevel
                if (typeof idx !== 'number') return ''
                return this.soundEmojis[idx] ?? ''
            }
        }
    }
</script>

<template>
    <!-- TODO: add your template code here. Use span element. --> 
     <span>{{ emoji }}</span>

</template>