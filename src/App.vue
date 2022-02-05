<template>
<div class="top-barr">
  <Navegation/>
    <router-link to="/" class="logo">Github Profiles
    <img src="@/assets/logo.png" alt="logo">
    </router-link>
</div>
  <router-view/>
  <footer class="footer">
    <p>Application made by Jansel Roa with Vuejs💚 and the github <a href="https://docs.github.com/en/rest" target="_blank">api</a></p>
    <p><a href="https://github.com/janseroa/githubList" target="_blank">Repository of code</a></p>
  </footer>
</template>
<script>
import Navegation from "@/components/Navegation.vue"
export default {
  name:"App",
  components:{
    Navegation
  }
}
</script>
<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');
/*base*/
a{
  text-decoration: none;
  color:#000;
}
ul{
  list-style: none;
}
body{
  margin: 0;
  font-family: 'Lato', sans-serif;
  overflow-x: hidden;
}



h1,h2  {
  text-align: center;
}
.footer{
  margin-top:100px;
  border-top: 1px solid #ddd;
  position: relative;
  text-align: center;
  bottom: 0;
  width: 100%;
  padding: 20px 0;
  a{
    text-decoration: underline;
  }
}

.search {
  display: block;
  width: 80%;
  border: 1px solid #ddd;
  padding: 10px;
  margin: 30px auto;
}
.container {
  width: 100%;
  justify-content: center;
  display: flex;
  flex-wrap: wrap;
}
.item{
    width: 300px;
    margin: 10px;
}
.top-barr{
  width: 100%;
  background-color: #fff;
  height: 50px;
  padding-bottom:10px;
  margin-bottom: 50px;
  border-bottom: 1px solid #ddd;
}
.logo{
  position: absolute;
  top: 10px;
  left: 10px;
  font-size:1.7rem;
  font-weight:bold;
  display:flex;
  img{
    display: inline-block;
    width: 40px;
    margin-left: 20px;
  }
}
</style>
