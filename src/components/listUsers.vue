<template>
    <div class="item" @click="$emit('getUser')">
        <h2>{{name}}</h2>
        <img :src="img" alt="github user">
    </div>
</template>
<script>
export default {
    name:"listUser",
    props:["name","img"]
}
</script>
<style lang="scss" scoped>
.item{
    transition: transform, 0.8s;
}
.item:hover{
    transform: scale(0.9);
    cursor: pointer;
    color:#555;
}
img{
    width: 100%;
}
</style>