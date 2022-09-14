<template>
<div id="appstyle">
  <div class="row">
    <div class="col">
      <h3 class="text-center mb-5">Prijava</h3>
    </div>
  </div>
  <div class="row">
      <div class="col">
      </div>
      <div class="col">
        <form @submit.prevent="login">
          <div class="form-group">
            <label for="exampleInputEmail1">Email adresa</label>
            <input v-model="email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Unesite Email">
            
          </div>
          <div class="form-group">
            <label for="exampleInputPassword1">Lozinka</label>
            <input v-model="password" type="password" class="form-control" id="exampleInputPassword1" placeholder="Lozinka">
          </div>
          <button type="submit" class="btn btn-primary mt-5">Login</button>
        </form>
      </div>
      <div class="col">
      </div>
    </div>
  </div>
</template>

<script>
import {signInWithEmailAndPassword } from "firebase/auth";
import {auth} from '@/firebase.js'
export default {
  data () {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    login () {
      signInWithEmailAndPassword(auth, this.email, this.password)
  .then((userCredential) => {
    const user = userCredential.user;
  })
  .catch((error) => {
    const errorCode = error.code;
    const errorMessage = error.message;
  });
    }
  }
}
</script>
