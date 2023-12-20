<template>
    <div class="single-card">
        <div class="card" style="width: 18rem;">
            <img :src="props.article.urlToImage" class="card-img-top" alt="news-img">
            <div class="card-body">
                <h5 class="card-title"> {{ props.article.title }}</h5>
                <p class="card-text">{{ props.article.description }}</p>
                <a :href="props.article.url" class="btn btn-primary">Go somewhere</a>
            </div>
        </div> 
        <!-- <p>{{ props.article.urlToImage }}</p> -->

    </div>
</template>

<script setup>
    import { defineProps } from 'vue'

    const props = defineProps(['article'])

</script>

<style scoped>
    .single-card{
        margin: 1px 0 20px 0;
        break-inside: avoid;
    }

</style>