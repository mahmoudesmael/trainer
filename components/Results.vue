<template>
    <v-row justify="center" class="ma-5">
        <div class="font-weight-bold ">your score || {{ score }}</div>
    </v-row>
</template>

<script>
export default {
    props: ['score'],
};
</script>

<style></style>
