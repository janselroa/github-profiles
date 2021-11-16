<template>
    <nav :class="{'dark-mode':darkMode,'nav':true}">
        <h1>Github profiles</h1>
        
        <button @click="activeDarkMode" class="btn-darkMode"><div :class="{'activate':isActive}"></div></button>
        </nav>    
</template>
<script>
export default{
data(){
    return{
        darkMode:false,
        isActive:false,
    }
},
methods:{
    activeDarkMode(){
        this.isActive=!this.isActive;
        this.darkMode=!this.darkMode;
        this.$emit("darkMode");
    }
}
}
</script>
<style scoped>
.nav{
    width: 100%;
    padding:10px 0;
    box-shadow: 5px 5px 5px #dddd;
    --bg-color:#fff;
    --text-color:#000;
    --mode:#e5f1ff;
    --mode2:hsl(214, 100%, 50%);
    background-color:var(--bg-color);
    color: var(--text-color);
}
h1{
    padding:5px;
    margin: 0;
}
.btn-darkMode{
    position: absolute;
    top: 10px;
    right: 20px;
    width: 100px;
    height: 35px;
    border: none;
    border-radius: 100px;
    margin: 5px;
    background-color:var(--mode);
}
.btn-darkMode div{
    position: absolute;
    top: 5px;
    left: 5px;
    width:25px;
    height: 25px;
    background-color: var(--mode2);
    border-radius: 100px;
    transition: left .7s;
}

.activate{
    left:70px !important;
}
.dark-mode{
    --bg-color:#333;
    --mode:#555;
    --mode2:#fff;
    --text-color:#fff;
    box-shadow: 5px 5px 5px #11111163;
    }
</style>
