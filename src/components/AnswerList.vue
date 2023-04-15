<template>

    <h3>You would rather...</h3>

    <ul>
        <li v-for="answer in answers">{{ answer }}</li>
    </ul>

</template>

<script>
export default {
    name: 'AnswerList',
    props: {
        answers: Array
    }
}
</script>

<style scoped>
    ul {
        list-style-position: inside;
    }
</style>