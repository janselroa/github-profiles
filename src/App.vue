<template>
  <div id="nav">
    <router-link to="/" class="logo">Github Profiles
    <img src="@/assets/logo.png" alt="logo">
    </router-link>
    <router-link to="/">Home</router-link>|
    <router-link to="/proyects">Featured projects</router-link>| 
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
  <footer class="footer">
    <p>Application made by Jansel Roa with Vuejs💚 and the github <a href="https://docs.github.com/en/rest" target="_blank">api</a></p>
    <p><a href="https://github.com/janseroa/githubList" target="_blank">Repository of code</a></p>
  </footer>
</template>

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

#nav {
  padding: 20px;
  text-align: center;
  border-bottom: 1px solid #ddd;
  a {
    font-size:1.3rem;
    margin: 10px;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
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
.logo{
  position: absolute;
  top: 5px;
  left: 10px;
  font-size:2rem;
  font-weight:bold;
  display:flex;
  img{
    display: inline-block;
    width: 40px;
    margin-left: 20px;
    margin-top: -4px;
  }
}
</style>
