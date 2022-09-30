<template>
    <div>
        <!-- Container -->
        <div class="container mx-auto text-center">
            <h1 class="mt-10 font-semibold">There is 10 question here</h1>
            <p>Your correct answers : {{correctCount}}/{{totalCount}}</p>
            <!-- Question -->
            <h1 class="my-10 mx-[2rem] font-bold">{{index + 1}}-{{cQuestion.question}}</h1>

            <hr class="mb-10">

            <!-- Answers container -->
            <div class="grid md:grid-cols-2 place-items-center md:mx-[-1.25rem] lg:mx-[5rem] xl:mx-[13rem]">

                <!-- answer buttons -->
                <button v-for="(answer, i) in shuffledAnswers" :key="i" @click="changeIndex(i)" :class="correctFunc(i)"
                    class="w-[25rem] h-[6rem] rounded-tr-lg rounded-bl-lg bg-violet-400 transition duration-500 hover:scale-90 mb-3 md:mb-[5rem]">
                    <p class="text-center px-2 py-7">{{answer}}</p>
                </button>

            </div>

            <!-- Buttons -->
            <div class="flex flex-row items-center justify-center my-5">
                <!-- Submit button -->
                <button class="w-[9rem] h-[3rem] bg-violet-600 mr-5 rounded-full" @click="submitAnswer"
                    :disabled="cIndex === null || answered">
                    <p class="text-center px-2 py-1 text-white">Submit</p>
                </button>
                <!-- Next button -->
                <button class="w-[9rem] h-[3rem] bg-green-500 rounded-full" @click="next" :disabled="index===9">
                    <p class="text-center px-2 py-1 text-white">Next</p>
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.correct {
    background-color: lightgreen;
}

.incorrect {
    background-color: red;
}

.selected {
    background-color: #CD4EC5;
}
</style>


<script>
import _ from "lodash";

export default {
    name: 'ContentSection',
    props: {
        cQuestion: Object,
        next: Function,
        index: Number,
        increment: Function,
        correctCount: Number,
        totalCount: Number,
    },

    data() {
        return {
            cIndex: null,
            shuffledAnswers: [],
            correctAnswer: null,
            answered: false,
        }
    },

    methods: {
        changeIndex(index) {
            this.cIndex = index;
        },
        shuffleAnswer() {
            let answers = [...this.cQuestion.incorrect_answers, this.cQuestion.correct_answer]
            this.shuffledAnswers = _.shuffle(answers)
            this.correctAnswer = this.shuffledAnswers.indexOf(this.cQuestion.correct_answer);
        },
        submitAnswer() {
            let is_correct = false;
            if (this.cIndex == this.correctAnswer) {
                is_correct = true;
            }
            this.increment(is_correct);
            this.answered = true;
        },
        correctFunc(index) {
            let answerClass = ''
            if (!this.answered && this.cIndex === index) {
                answerClass = 'selected';

            } else if (this.answered && index === this.correctAnswer) {
                answerClass = 'correct';

            } else if (this.answered && index === this.cIndex && index !== this.correctAnswer) {
                answerClass = 'incorrect';
            }
            return answerClass;
        },
    },

    watch: {
        cQuestion: {
            immediate: true,
            handler() {
                this.cIndex = null;
                this.answered = null;
                this.correctAnswer = null;
                this.shuffleAnswer();

            }
        },
    },

    computed: {
        answers() {
            let answers = [...this.cQuestion.incorrect_answers];
            answers.push(this.cQuestion.correct_answer);
            return answers;
        }
    },

}
</script>

