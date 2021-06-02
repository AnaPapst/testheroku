<template>
  <div class="in-tech__banner index">
    <p>Oi, você quer descobrir como criar um portfólio incrível e aprender os primeiros passos para se entrar na área de tecnologia?</p>
    <p class="text-center">Confira nossos cursos!</p>
    <img src="../images/wecan.png">
  </div>
</template>

<script>
import UserService from '../services/user.service';

export default {
  name: 'Home',
  data() {
    return {
      content: ''
    };
  },
  mounted() {
    UserService.getPublicContent().then(
      response => {
        this.content = response.data;
      },
      error => {
        this.content =
          (error.response && error.response.data) ||
          error.message ||
          error.toString();
      }
    );
  }
};
</script>

<style>
    .in-tech__nav {
      font-size: 16px;
    }

    .alerta-erro {
      color: red;
    }

    .in-tech__banner.index {
        margin: 2rem 8%;
    }

    .in-tech__banner.index img {
        width: 100%;
        border-radius: 20px;
    }
</style>