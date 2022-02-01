<template>
  <div class="about">
    <h1>Page made by janselroa</h1>
    <UserComponent :userData="userData" :repos="repos"></UserComponent>
  </div>
</template>
<script>
import {ref} from 'vue'
import Service from '@/services/Service.js'
import UserComponent from '@/components/UserComponent.vue'
export default {
  components:{
        UserComponent
  },
  setup() {
    const userData = ref({})
    const repos = ref([])
    Service.get('users/janselroa').then(data=>userData.value=data.data)
    Service.get('users/janselroa/repos').then(data=>{
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
  },
}
</script>
