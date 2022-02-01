<template>
  <input
    v-model="search"
    class="search"
    type="search"
    placeholder="Username: "
  />
  <h1>Perfiles mas destacados</h1>
  <div class="container" v-if="!error">
    <listUsers
      v-for="user in listUsers"
      :key="user.id"
      :img="user.avatar_url"
      :url="user.html_url"
      :name="user.login"
      @getUser="getUser(user.login)"
    ></listUsers>
  </div>
  <p v-else>Usuario no encontrado {{ search }}</p>
</template>

<script>
// @ is an alias to /src
import listUsers from "@/components/listUsers.vue";
import { ref, watch } from "vue";
import { useRouter } from "vue-router";
import Service from "@/services/Service.js";
export default {
  name: "Home",
  components: {
    listUsers,
  },
  setup() {
    const router = useRouter();
    const search = ref("");
    const listUsers = ref([]);
    const error = ref("");
    const getUser = (username) => {
      router.push({
        name: "User",
        params: { username },
      });
    };
    Service.get("users").then((users) => (listUsers.value = users.data));
    watch(search, (newValue) => {
      Service.get(`search/users?q=${newValue}`)
        .then((users) => {
          listUsers.value = users.data.items;
          error.value = false;
        })
        .catch((err) => (error.value = err));
    });
    return { listUsers, search, error, getUser };
  },
};
</script>
<style lang="scss" scoped>

p {
  text-align: center;
  font-size: 1.4rem;
}
</style>
