<template>
    <div class="card text-white bg-danger">
        <div class="card-body text-center">
            <h1 class="card-title">Wrong!</h1>
            <hr>
            <button class="btn btn-primary" @click="backToQuestion()">Try again!</button>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'WrongAnswer',
        methods: {
            backToQuestion() {
                this.$emit('componentChanged','app-question');
            }
        },
    }
</script>