<template>
  <ul>
    <li v-for="(user, index) in users" :key="user.id" @click = "removeUser(index)">{{user.name}}</li>
  </ul>
</template>
<style scoped>
  ul{
    margin-top: 20px;
  }
  li{
    cursor: pointer;
    display:block;
    max-width: 200px;
    border-radius: 10px;
    box-shadow:1px 1px 2px #7f828b;
    margin-bottom: 10px;
    padding: 10px;
  }
</style>

<script>
  export default {
    async asyncData ({store}){
      await store.dispatch('getUsers');
      return {
        users: store.getters.users
      }
    },
    methods:{
      removeUser(id){
        this.$store.dispatch('removeUser', id);
        this.users = this.$store.getters.users;
      }
    }
  }
</script>
