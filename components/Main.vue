<template>
    <v-container>
        <h1 class="display-1 font-weight-bold text--secondary text-center ma-5">
            Ninja Reaction Timer
        </h1>
        <v-row justify="center">
            <v-btn
                class="white--text"
                color="pink"
                depressed
                @click="start"
                :disabled="isPlaying"
                >{{ button }}
            </v-btn>
        </v-row>
        <Block v-if="isPlaying" :delay="delay" @end="endGame" />
        <Results v-if="score" :score="score" />
    </v-container>
</template>

<script>
import Block from './Block';
import Results from './Results';

export default {
    name: 'Main',
    components: { Block },
    data() {
        return {
            isPlaying: false,
            delay: null,
            score: null,
            button: 'play',
        };
    },
    methods: {
        start() {
            this.delay = 2000 + Math.random() * 5000;
            this.isPlaying = true;
            this.score = null;
        },
        endGame(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            console.log(this.score);
            this.button = 'play againg';
        },
    },
};
</script>
