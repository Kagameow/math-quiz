<template>
    <div class="card text-center">
        <div class="card-header">
            What's {{firstNumber}} {{expressionType}} {{secondNumber}} = ?
        </div>
        <div class="card-body">
            <div class="row" style="margin-bottom: 15px">
                <div class="col">
                    <button class="btn btn-primary" @click="answerChecker($event)">{{variantsStorage[0]}}</button>
                </div>
                <div class="col">
                    <button class="btn btn-primary" @click="answerChecker($event)">{{variantsStorage[1]}}</button>
                </div>
            </div>
            <div class="row">
                <div class="col">
                    <button class="btn btn-primary" @click="answerChecker($event)">{{variantsStorage[2]}}</button>
                </div>
                <div class="col">
                    <button class="btn btn-primary" @click="answerChecker($event)">{{variantsStorage[3]}}</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Question',
        data() {
            return {
                operationMaxNumber: 100,
                questionExpression: 1,
                expressionType: '+',
                answer: 0,
                numberOfVariants: 4,
                variantsStorage: [],
                realAnswerIndex: 0,
                firstNumber: 0,
                secondNumber: 0
            }
        },
        methods: {
            numberGenerator() {
                return Math.floor(Math.random() * this.operationMaxNumber) + 1;
            },
            generateExpressionNumbers(){
                this.firstNumber = this.numberGenerator();
                this.secondNumber = this.numberGenerator();
            },
            typeRandomizer() {
                if (Math.random() > 0.500) {
                    this.expressionType = '+';
                } else {
                    this.expressionType = '-';
                }
            },
            calculateRightAnswer() {
                this.answer = this.expressionType === '+' ? this.firstNumber + this.secondNumber : this.firstNumber - this.secondNumber;
            },
            generateWrongAnswer() {
                let wrongNumber = 0;
                if (this.expressionType === '+') {
                    wrongNumber = Math.floor(Math.random() * this.operationMaxNumber * 2) + 1;
                } else {
                    let negativeOrPositiveMultiplier = Math.random() > 0.500 ? 1 : -1;
                    wrongNumber = (Math.floor(Math.random() * this.operationMaxNumber) + 1) * negativeOrPositiveMultiplier;
                }
                if (wrongNumber === this.answer) {
                    this.generateWrongAnswer();
                } else {
                    return wrongNumber;
                }
            },
            fillVariantsStorage() {
                this.realAnswerIndex = Math.floor(Math.random() * this.numberOfVariants);
                for (let i = 0; i < this.numberOfVariants; i++) {
                    if (i !== this.realAnswerIndex) {
                        this.variantsStorage.push(this.generateWrongAnswer())
                    } else {
                        this.variantsStorage.push(this.answer)
                    }
                }
            },
            initAllValues() {
                this.generateExpressionNumbers();
                this.typeRandomizer();
                this.calculateRightAnswer();
                this.fillVariantsStorage();
                console.log(this.answer);
            },
            resetAllValues(){
              this.variantsStorage = [];
              this.initAllValues();
            },
            answerChecker(event) {
                if (+event.target.innerText !== this.answer) {
                    this.$emit('componentChanged','app-wrong-answer');
                } else {
                    this.$emit('componentChanged','app-right-answer');
                    this.resetAllValues();
                }
            }
        },
        computed: {
            firstNumberGenerator() {
                return Math.floor(Math.random() * this.operationMaxNumber) + 1;
            },
            secondNumberGenerator() {
                return Math.floor(Math.random() * this.operationMaxNumber) + 1;
            }
        },
        created() {
            this.initAllValues();
        }
    }
</script>
