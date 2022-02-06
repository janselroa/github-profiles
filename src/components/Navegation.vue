<template>
    <nav class="nav" :class="{'menu-show':menuShow}">
    <img class="close-icon"  @click="menuShow=false" src="@/assets/close-icon.svg" alt="close icon">
    <router-link @click="menuShow=false" class="link" to="/">Home</router-link>
    <router-link  @click="menuShow=false" class="link" to="/proyects">Featured projects</router-link>
    <router-link  @click="menuShow=false" class="link" to="/about">About</router-link>
    </nav>
    <img @click="menuShow=!menuShow" src="@/assets/icon-menu.svg" alt="icon menu" class="icon-menu">
</template>
<script>
import {ref} from "vue"
export default {
    setup() {
        const menuShow = ref(false)
        return{menuShow}
    },
}
</script>
<style lang="scss" scoped>
.nav {
    width: 100%;
    position: absolute;
    top: 0;
    padding: 20px;
    text-align: center;
  a {
    font-size:1.3rem;
    margin: 10px;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
img{
    display: none;
}
@media screen and (max-width:700px){
    .nav{
        height:100vh;
        width:100%;
        position: absolute;
        left: 0;
        top: 0;       
        z-index: 10;
        background-color: #fff;
        display:none;
        padding:0;
    }
    .link{
        display: block;
        padding:10px 0;
    }
    .icon-menu{
        display: block
    }
}
.icon-menu{
    position: absolute;
    top: 5px;
    right: 10px;
    width:40px;
    height: 40px;
}
.menu-show{
    display: block;
    img{
        display: block;
        padding:10px;
    }
}
</style>