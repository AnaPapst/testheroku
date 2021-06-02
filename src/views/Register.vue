<template>
  <div class="in-tech__form">
    <div class="container">
      <div class="in-tech__form--title">
          <h1>Bem vinda!</h1>
      </div>

      <form class="in-tech__form__content" name="form" @submit.prevent="handleRegister">
        <div class="in-tech__form__content--input form-group" v-if="!successful">
          <div class="form-group">
            <label for="username">Username</label>
            <input
              v-model="user.username"
              v-validate="'required|min:3|max:20'"
              type="text"
              class="form-control"
              name="username"
            />
            <div
              v-if="submitted && errors.has('username')"
              class="alerta-erro"
            >{{errors.first('username')}}</div>
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input
              v-model="user.email"
              v-validate="'required|email|max:50'"
              type="email"
              class="form-control"
              name="email"
            />
            <div
              v-if="submitted && errors.has('email')"
              class="alerta-erro"
            >{{errors.first('email')}}</div>
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              v-model="user.password"
              v-validate="'required|min:6|max:40'"
              type="password"
              class="form-control"
              name="password"
            />
            <div
              v-if="submitted && errors.has('password')"
              class="alerta-erro"
            >{{errors.first('password')}}</div>
          </div>
          <div class="in-tech__form__content--btn">
            <button class="in-tech__btn btn">Enviar</button>
          </div>
        </div>
      </form>

      <div
        v-if="message"
        class="sucesso"
        :class="successful ? 'alert-success' : 'alerta-erro'"
      >{{message}}</div>
    </div>
  </div>
</template>

<script>
import User from '../models/user';

export default {
  name: 'Register',
  data() {
    return {
      user: new User('', '', ''),
      submitted: false,
      successful: false,
      message: ''
    };
  },
  computed: {
    loggedIn() {
      return this.$store.state.auth.status.loggedIn;
    }
  },
  mounted() {
    if (this.loggedIn) {
      this.$router.push('/profile');
    }
  },
  methods: {
    handleRegister() {
      this.message = '';
      this.submitted = true;
      this.$validator.validate().then(isValid => {
        if (isValid) {
          this.$store.dispatch('auth/register', this.user).then(
            data => {
              this.message = data.message;
              this.successful = true;
            },
            error => {
              this.message =
                (error.response && error.response.data) ||
                error.message ||
                error.toString();
              this.successful = false;
            }
          );
        }
      });
    }
  }
};
</script>

<style>
    .sucesso {
      background-color: #caf7e3;
      padding: 2rem;
      border-radius: 15px;
      width: 50%;
      margin: auto;
    }

    .alert {
      padding: 0;
      color: #bfb051;
    }

    .form-group label {
      z-index: 1;
    }

    .in-tech__btn {
      background-color: #435560 !important;
      color: white !important;
    }

   .in-tech__form {
        margin: 4rem 0;
    }

    .in-tech__form--title h1 {
        padding-bottom: .5rem;
        font-size: 1rem;
        text-align: center;
        position: relative;
    }

    .in-tech__form__content {
        padding: 2rem 13rem;
    }

    .in-tech__form__content--input {
        margin-bottom: 1.5rem;
    }

    .in-tech__form__content--input label {
        position: absolute;
        margin: -15px 0 0 10px;
    }

    .in-tech__form__content--input input {
        background-color: #FBE0DC;
        border: none;
    }

    .in-tech__form__content--btn {
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .in-tech__btn {
        width: 100px;

        background-color: black;
        color: white;
        border-color: none;
    }
</style>
