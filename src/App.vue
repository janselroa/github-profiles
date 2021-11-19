<template>
  <div id="app" :class="{'darkMode':darkMode}">
    <Navigation @darkMode="activeDarkMode"></Navigation>
  <div class="container-input">
    <input v-model="username"  @keyup.enter="getUser" class="input" type="text" placeholder="Username: ">
    <button @click="getUser">Search</button>
  </div>
  <div class="userInfo" v-if="github!=null">
    <h2>{{github.name}}</h2>
    <div class="userInfo__content">
      <img :src="github.avatar_url">
      <div>
        <p>Bio: {{github.bio}}</p>
        <p>followers: {{github.followers}}</p>
        <p>following: {{github.following}}</p>
        <p>Count Repositories: {{github.public_repos}}</p>
      </div>
      <div>
        <p>Newest Repositories</p>
        <p v-for="repo in github_repos" :key="repo.id"><a :href="repo.html_url">{{repo.full_name}}</a></p>
      </div>
    </div>
  </div>
        <div class="error" v-if="error">
          <p>
          the User {{username}} not found
          </p>
        </div>
        <Footer  :class="{'darkMode':darkMode}"></Footer>
  </div>
</template>

<script>
import Footer from "@/components/Footer.vue";
import Navigation from "@/components/Navegation.vue";
export default {
  name: 'App',
  components: {
    Navigation,
    Footer,
  },
  data(){
    return{
      darkMode:false,
      username:"",
      github:null,
      github_repos:null,
    error:"",
    }
  },
  methods: {
    activeDarkMode(){
      this.darkMode=!this.darkMode;
    },
    getUser(){
      fetch(`https://api.github.com/users/${this.username}`)
      .then(res=>res.json()).then(data=>this.github=data)
      .catch((err)=>{
          this.error=err
      })
      fetch(`https://api.github.com/users/${this.username}/repos`).then(res=>res.json()).then(data=>{
       try{
          data.sort((a,b)=>{
             
            if (a.created_at < b.created_at) {
              return 1;
            }
            if (a.created_at > b.created_at) {
              return -1;
            }
            return 0;
          })
          this.github_repos=data.slice(0,5);
        }catch (e) {
          this.error=e;
          this.github=null;
          this.github_repos=null;
        }
        console.log(this.github_repos)
      })
    }
  }
}
</script>

<style>
body{
  --bg-color:#fff;
  --text-color:#000;
  margin: 0;
}
#app {
  background-color: var(--bg-color);
  display: flex;
  flex-direction: column;
  height:100vh;
  margin: 0;
  font-family: "Roboto";
  color:var(--text-color)
}
.darkMode{
  --bg-color:#333;
  --text-color:#fff;
}
.container-input{
  width:300px;
  margin:100px auto;
}
input,.container-input button{
  border: none;
  outline: none;
  padding: 10px;
}
.input{
  background-color:#eeee;
}
.container-input button{
  background-color:hsl(214, 100%, 50%);
  color: #fff;
}
.darkMode button{
  background-color:hsl(0, 0%, 10%);
 
}
h2{
  text-align: center;
}
.userInfo{
  width: 100%;
  background-color:var(--bg-color)
}
.userInfo__content{
  display: flex;
  width: 100%;
  flex-wrap: wrap;
  justify-content: center;
  font-weight: 600;
  font-size:18px;

}
.userInfo__content img{
  width: 300px;
  object-fit: cover;
}
.userInfo__content div{
  width:200px;
  margin-left: 20px;
}
.userInfo__content a{
  color: var(--text-color);
}
.footer{
  padding-top:150px;
  background-color: var(--bg-color);
color:var(--text-color);
}
.error{
  color: #f00;
  background-color: rgb(255, 115, 115);
}
</style>
