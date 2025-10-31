/IS216 WAD2/exercises/week10-ice-yujjjia/src/components/subcomponents/TaskTracker.vue
<script>
export default {
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
        markAsDone(index) {
            this.$emit('delete-task', index)
        }
    }
}
</script>

<template>
    <div class="row">
        <div class="col-md-4" v-for="(task, index) in tasks" :key="index">
            <div class="card mb-3">
                <div class="card-body">
                    <h6 class="card-subtitle mb-2 text-muted">Deadline: {{ task.deadline }}</h6>
                    <p class="card-text">{{ task.desc }}</p>
                    <button type="button" class="btn btn-primary btn-sm" @click="markAsDone(index)">Done</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
</style>