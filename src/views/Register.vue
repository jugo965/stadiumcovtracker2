<template>
  <div id="appstyle">
    <div class="row">
      <div class="col">
        <h3 class="text-center mb-5">Registracija</h3>
      </div>
    </div>
    <div class="row">
      <div class="col"></div>
      <div class="col">
        <form @submit.prevent="signup">
          <div v-if="errorMessage" class="alert alert-danger">
            <strong>Ups!</strong>
            {{ errorMessage }}
          </div>
          <div class="form-group">
            <label for="emailField">Email adresa</label>
            <input
              v-model="email"
              type="email"
              class="form-control"
              id="emailField"
              aria-describedby="emailHelp"
              placeholder="Unesite Email"
            />
          </div>
          <div class="form-group">
            <label for="passwordField">Lozinka</label>
            <input
              v-model="password"
              type="password"
              class="form-control"
              id="passwordField"
              placeholder="Lozinka"
            />
          </div>
          <div class="form-group">
            <label for="confirmPasswordField">Potvrda lozinke</label>
            <input
              v-model="password2"
              type="password"
              class="form-control"
              id="confirmPasswordField"
              placeholder="Potvrda lozinke"
            />
          </div>

          <form>
</form>



          <button type="submit" class="btn btn-primary mt-5">Register</button>
        </form>
      </div>
      <div class="col"></div>
    </div>
  </div>
</template>
<script>
import {auth} from "@/firebase.js"
import { createUserWithEmailAndPassword } from 'firebase/auth';
export default {
  data() {
    return {
      errorMessage: "",
      email: "",
      password: "",
      password2: "",

    };
  },
  mounted() {},
  methods: {
    signup() {
      createUserWithEmailAndPassword(auth, this.email, this.password).catch(error => {
          console.error(error);
          this.errorMessage = error.message;
        });
    }
  }
};
</script>