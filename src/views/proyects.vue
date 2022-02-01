<template>
    <input type="search" placeholder="Search repo " class="search" v-model="search">
        <p>Results found: {{results}}</p>
    <div class="container">
        <a v-for="repo in repos" :key="repo.id" class="item" :href="repo.html_url" target="_blank">
            <h2>{{repo.name}}</h2>
            <p>{{repo.description}}</p>
            <br>
            <p>By {{repo.owner.login}}</p>
        </a>
    </div>
</template>
<script>
import {ref,watch} from 'vue'
import Service from '@/services/Service.js'
export default {
    setup() {
        const repos = ref([])
        const search = ref("github-profiles")
        const results = ref(0)
        const getRepos = (dato)=>{

            Service.get(`search/repositories?q=${dato}`).then(data=>{
                results.value=data.data.total_count
            repos.value=data.data.items
        })
        }
        getRepos(search.value)
        watch(search,(newValue)=>{
            getRepos(newValue)
        })
        
        return {repos, search,results}
    },
}
</script>
<style scoped>
.item{
    text-align: center;
}
p{
    text-align: center;
}
a{
    display: block;
}
.item{
    padding:20px;
    box-shadow: 0px 0px 20px #ddd;
}
</style>