<template>
    <v-row justify="center" v-if="showBlock" @click="stopTimer">
        <v-col cols="6">
            <div class="square">click me</div>
        </v-col>
    </v-row>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        };
    },
    mounted() {
        console.log('component mounted');
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay);
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.$emit('end', this.reactionTime);
        },
    },
};
</script>

<style>
.square {
    padding: 100px !important;
    color: white !important;
    background-color: #27ae60 !important;
    padding: 20px !important;
    text-align: center !important;
    margin: 20px !important;
    border-radius: 20px !important;
}
</style>
