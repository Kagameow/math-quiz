<template>
    <div id="app" class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 offset-md-2 col-md-6 offset-md-3">
                <h1 class="text-center">Math Quiz</h1>
            </div>
        </div>
        <hr>
        <div class="col-xs-12 col-sm-8 offset-md-2 col-md-6 offset-md-3">
            <Question/>
        </div>
    </div>
</template>

<script>

    import Question from "@/components/Question";

    export default {
        name: 'App',
        components: {Question}
    }
</script>

