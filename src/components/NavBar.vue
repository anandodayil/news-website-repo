<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <a class="navbar-brand anand" href="#" @click="articleFilterAPI('')">
            <img src="../assets/headlineNewsLogo.png" height="30px" width="75px"/>
        </a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item text-primary">
                    <a class="nav-link" href="#" @click="articleFilterAPI('ipl')">IPL</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#" @click="articleFilterAPI(finance)">Finance</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" @click="articleFilterAPI('politics')">Politics</a>
                </li>
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" role="button" data-toggle="dropdown" aria-expanded="false">
                        Dropdown
                    </a>
                    <div class="dropdown-menu">
                        <a class="dropdown-item" href="#">Action</a>
                        <a class="dropdown-item" href="#">Another action</a>
                        <div class="dropdown-divider"></div>
                        <a class="dropdown-item" href="#">Something else here</a>
                    </div>
                </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
                <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search"
                    v-model="newsArticle">
                <button class="btn btn-outline-success my-2 my-sm-0" @click="sendArticleName">Search</button>
            </form>
        </div>
    </nav>
</template>

<script setup>
    import { ref, defineEmits } from 'vue'

    const newsArticle = ref('')

    const emits = defineEmits(['send-news-article'])

    const articleFilterAPI = (articleFilter) => {
        emits('send-news-article', articleFilter)
    }

    const sendArticleName = () => {
        emits('send-news-article', newsArticle.value)
    }
</script>

<style scoped>
    .anand{
        padding: 0
    }
    .navbar{
        margin-bottom: 10px;
    }
</style>