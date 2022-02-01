<template>
<div class="container">
    <img :src="userData.avatar_url" alt="avatar">
    <div class="container__content">
    <h1>{{userData.name}}</h1>
    <p>{{userData.bio}}</p>
        <p>Public Repositorys: {{userData.public_repos}}</p>
        <p>followers: {{userData.followers}}</p>
        <p>following: {{userData.following}}</p>
        <p><a :href="userData.html_url">Url Profile</a></p>
        <p>Location: {{userData.location}}</p>
    </div>
    <div class="container__content">
        <p>Newest Repositories</p>
        <p v-for="repo in repos" :key="repo.id"><a :href="repo.html_url">{{repo.full_name}}</a></p>
    </div>
</div>
</template>
<script>
export default {
    name:"UserComponent",
    props:["userData","repos"]
}
</script>

<style lang="scss" scoped>
.container {
    margin: auto;
    margin-top: 100px;
    img{
        width: 400px;
    }
    p{
        font-size: 1.3rem
    }
    a{
        text-decoration: underline;
    }
    div{
        margin: 20px;
    }
}

</style>