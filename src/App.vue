<template>
    <div id="app" class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 offset-md-2 col-md-6 offset-md-3">
                <h1 class="text-center">Math Quiz</h1>
            </div>
        </div>
        <hr>
        <div class="col-xs-12 col-sm-8 offset-md-2 col-md-6 offset-md-3">
                <component @componentChanged="activeComponent = $event" :is="activeComponent"></component>
        </div>
    </div>
</template>

<script>

    import Question from "@/components/Question";
    import RightAnswer from "@/components/RightAnswer";

    export default {
        name: 'App',
        components: {
            appRightAnswer: RightAnswer,
            appQuestion: Question
        },
        data() {
            return {
                activeComponent: 'app-question'
            }
        },
    }
</script>

