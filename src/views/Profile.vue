<template>
  <div class="user-board">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <header>
            <h3>
              Oi <strong>{{currentUser.username}}</strong>
            </h3>
          </header>
        </div>
        <div class="col-12">
          <p>
            <strong>Token:</strong>
            {{currentUser.accessToken.substring(0, 20)}} ... {{currentUser.accessToken.substr(currentUser.accessToken.length - 20)}}
          </p>
          <p>
            <strong>Id:</strong>
            {{currentUser.id}}
          </p>
          <p>
            <strong>Email:</strong>
            {{currentUser.email}}
          </p>
          <strong>Tipo de usuário:  </strong> <span v-for="(role,index) in currentUser.roles" :key="index">{{role}}</span>
          <!-- <ul>
            <li v-for="(role,index) in currentUser.roles" :key="index">{{role}}</li>
          </ul> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Profile',
  computed: {
    currentUser() {
      return this.$store.state.auth.user;
    }
  },
  mounted() {
    if (!this.currentUser) {
      this.$router.push('/login');
    }
  }
};
</script>

<style>
.user-board {
  padding: 3rem;
}
</style>
