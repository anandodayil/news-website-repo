<template>
  <div class="anand">
    <NavBar @send-news-article="sendNewsArticleHandler"></NavBar>
    <CardContainer :newsArticle="newsArticle"></CardContainer>
  </div>
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
  .anand{
    background-color: lightgray;
  }
</style>
