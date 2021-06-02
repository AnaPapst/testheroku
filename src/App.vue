<template>
  <div class="in-tech">
    <main class="in-tech__body">
      <header class="in-tech__nav">
        <nav class="in-tech__nav--padding navbar navbar-expand-lg navbar-light">
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarTogglerDemo01"
            aria-controls="navbarTogglerDemo01" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          
          <div class="collapse navbar-collapse" id="navbarTogglerDemo01">
            <router-link to="/home" class="nav-link">
              <a class="in-tech__nav--title navbar-brand">
                We &#60; <font-awesome-icon icon="heart" style="color: red" /> /> tech
              </a>
            </router-link>
            <div class="navbar-nav mr-auto">
              <li class="nav-item">
              </li>
              <li v-if="showAdminBoard" class="nav-item">
                <router-link to="/admin" class="nav-link">Admin Board</router-link>
              </li>
              <li v-if="showModeratorBoard" class="nav-item">
                <router-link to="/mod" class="nav-link">Moderator Board</router-link>
              </li>
              <li class="nav-item">
                <router-link to="/aulas" class="nav-link">Aulas</router-link>
              </li>
              <li class="nav-item">
                <router-link to="/indique" class="nav-link">Indique uma amiga</router-link>
              </li>
            </div>
            <div v-if="!currentUser" class="navbar-nav ml-auto">
              <li class="nav-item">
                <router-link to="/register" class="nav-link">
                  <span class="in-tech__nav-btn light">Registrar</span>
                </router-link>
              </li>
              <li class="nav-item">
                <router-link to="/login" class="nav-link">
                <span class="in-tech__nav-btn login">Login</span>
                </router-link>
              </li>
            </div>
  
            <div v-if="currentUser" class="cta-btn navbar-nav ml-auto">
              <li class="nav-item">
                <router-link to="/profile" class="nav-link">
                  <span class="in-tech__nav-btn light"> Oi {{ currentUser.username }}!</span>
                </router-link>
              </li>
              <li class="nav-item">
                <a class="nav-link" href @click.prevent="logOut">
                  <span class="in-tech__nav-btn dark">Sair</span>
                </a>
              </li>
            </div>
          </div>
        </nav>
      </header>
      <router-view />
    </main>
  </div>
</template>

<!-- <font-awesome-icon icon="sign-in-alt" /> -->

<script>
export default {
  computed: {
    currentUser() {
      return this.$store.state.auth.user;
    },
    showAdminBoard() {
      if (this.currentUser && this.currentUser.roles) {
        return this.currentUser.roles.includes('ROLE_ADMIN');
      }

      return false;
    },
    showModeratorBoard() {
      if (this.currentUser && this.currentUser.roles) {
        return this.currentUser.roles.includes('ROLE_MODERATOR');
      }

      return false;
    }
  },
  methods: {
    logOut() {
      this.$store.dispatch('auth/logout');
      this.$router.push('/login');
    }
  }
};
</script>

<style Lang="scss">
  .in-tech__nav-btn {
    padding: 10px 20px;
    margin-right: 10px;
    background-color: #caf7e3;
    border-radius: 15px;
  }

  .in-tech__nav-btn.light {
    background-color: #caf7e3;
  }

  .in-tech__nav-btn.dark {
    background-color: #ff7171;
  }

  .in-tech__nav-btn.login {
    background-color: #e4bad4;
  }

  .bi-heart-fill {
    color: red;
    font-size: 1rem;
  }

  .in-tech {
    background: #FBE0DC;
    padding: 1rem;
  }

  .in-tech__body {
    min-height: calc(100vh - 6rem);
    border: 7px solid black;
    border-radius: 4rem;
    background-color: white;
  }

  .in-tech__nav {
    font-size: 12px;
  }

  .in-tech__nav--title {
    border: 3px solid;
    padding: .3rem 1rem .6rem 1rem;
    border-radius: 20px;
    font-weight: bold;
  }

  .in-tech__nav--padding {
    padding: 16px 3rem !important;
  }

  .in-tech__btn {
    font-size: 12px !important;

    border-radius: 16px !important;
  }

  .in-tech__login {
    margin-right: 1rem;
  }

  .in-tech__btn a {
    color: white;
  }

  .in-tech__login a {
    color: black;
  }

  .in-tech__form--title {
    position: relative;
  }

  .in-tech__form--title::after {
      content: '';
      width: 60px;
      height: 2px;
      position: absolute;
      background-color: green;
      bottom: 0;
      right: 0;
      left: 0;
      margin: auto;
  }

  @media (min-width:720px) {
    .in-tech {
        padding: 3rem;
    }
  }
</style>