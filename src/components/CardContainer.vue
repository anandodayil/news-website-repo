<template>

    <div class="card-container">
        <SingleCard v-for="(article, index) in allArticles" :key="index"
                :article="article"></SingleCard>
        <!-- <div class="row-of-four" v-for="(articleSet, indexSet) in newAllArticles" :key="indexSet">
            <SingleCard v-for="(article, index) in articleSet" :key="`${indexSet}${index}`"
                :article="article"></SingleCard>
        </div> -->
    </div>

</template>

<script setup>
import SingleCard from './SingleCard.vue';

import axios from 'axios'

import { ref, defineProps, watch } from 'vue'

const props = defineProps(['newsArticle'])
const apiKey = ref('66c57000d82b48bf908ad3f44d3c8271')
const allArticles = ref([])
// const newAllArticles = ref([])

watch(() => {
    allArticles.value
}, () => {
    for(let i = 0; i < allArticles.value.length; i++){
        if(allArticles.value[i].author === null){
            allArticles.value.splice(i, 1)
        }
    }
    // console.log(allArticles.value)
    // let tempArticlesSet = []
    // for(let i = 0; i < allArticles.value.length; i++){
    //     tempArticlesSet.push(allArticles.value[i])
    //     if((i + 1) % 4 === 0){
    //         newAllArticles.value.push(tempArticlesSet)
    //         tempArticlesSet = []
    //     }
    // }
}, {
    deep: true
})

watch(() => {
    props.newsArticle
}, () => {
    console.log(props.newsArticle)
    axios.get(`https://newsapi.org/v2/everything?q=${props.newsArticle}&apiKey=${apiKey.value}`)
        .then((response) => allArticles.value = response.data.articles.splice(0, 100))
        .catch((err) => console.log(err.message)) 
}, {
    deep: true
})



</script>

<style scoped>
    .card-container{
        columns: 4;
        column-gap: 10px;
        
    }

</style>