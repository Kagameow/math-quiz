<template>
    <div class="card text-white bg-success">
        <div class="card-body text-center">
            <h1 class="card-title">That's Correct!</h1>
            <hr>
            <button class="btn btn-primary" @click="nextQuestion()">Next one!</button>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'RightAnswer',
        methods: {
            nextQuestion() {
                this.$emit('componentChanged','app-question');
            }
        },
    }
</script>