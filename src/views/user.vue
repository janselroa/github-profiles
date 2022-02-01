<template>
<UserComponent :userData="userData" :repos="repos"></UserComponent>
</template>
<script>
import {ref} from 'vue'
import { useRoute } from 'vue-router'
import Service from '@/services/Service.js'
import UserComponent from '@/components/UserComponent.vue'
export default {
    name:"User",
    components:{
        UserComponent
    },
    setup(){
        const route = useRoute()
        const userData = ref({})
        const repos = ref([])
        const username = route.params.username
        Service.get(`users/${username}`).then(data=>userData.value=data.data)
        Service.get(`users/${username}/repos`).then(data=>{
             data.data.sort((a,b)=>{
             
            if (a.created_at < b.created_at) {
              return 1;
            }
            if (a.created_at > b.created_at) {
              return -1;
            }
            return 0;
            })

            repos.value=data.data.slice(0,5)
        })

        return{userData,repos}
    }
}
</script>
