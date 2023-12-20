<template>
    <NavBar @send-news-article="sendNewsArticleHandler"></NavBar>
    <CardContainer :newsArticle="newsArticle"></CardContainer>
</template>

<script setup>
import NavBar from './components/NavBar.vue';
import CardContainer from './components/CardContainer.vue';

import { ref } from 'vue'

const newsArticle = ref()

const sendNewsArticleHandler = (newsArticleFC) => {
  newsArticle.value = newsArticleFC
} 
</script>

<style scoped>

</style>
