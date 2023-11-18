<template>
  <div class="users">
    <UserCard v-for="user in users" :key="user.id" :user="user" />
  </div>
</template>

<script>
// @ is an alias to /src
import UserCard from "@/components/UserCard.vue";
import EventService from "@/services/EventService.js";

export default {
  name: "UserList",
  components: {
    UserCard,
  },
  data() {
    return {
      users: null,
    };
  },
  created() {
    EventService.getUsers()
      .then((response) => {
        this.users = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
.users {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
