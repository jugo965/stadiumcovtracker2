<template>
  <div id="app"> 
    <router-link class="navbar-brand" :to="{name: 'home'}">          
      <a id="title"> <b>StadiumCOVtracker</b></a>              
        </router-link>
          <div class="navbtns">
                  <router-link v-if="authenticated"  class="btn btn-outline nvb" to="/Unos">Unos gledatelja</router-link>
                  <router-link v-if="authenticated"  class="btn btn-outline nvb" to="/Pregled">Pregled gledatelja</router-link>
                  <router-link v-if="!authenticated"  class="btn btn-outline nvb" to="/Login">Login</router-link>
                <span v-if="authenticated">
                  <a @click="logout" id="logout" class="btn btn-outline logout" href="#">Logout</a>
                </span>
                <router-link v-if="!authenticated" class="btn btn-outline nvb" to="/Register">Register</router-link>
              </div>
        <router-view/>


  </div>
</template>

<script type="text/javascript">
import store from '@/store.js'
import {auth} from '@/firebase.js'
import {onAuthStateChanged, signOut} from "firebase/auth";

export default {
  data () {
    return store;
  },

  methods: {
    logout() {
      signOut(auth).then(() => {
  // Sign-out successful.
}).catch((error) => {
  // An error happened.
});
    }
  },

  
  mounted () {
    onAuthStateChanged(auth, (user) => {
      if (user) {
        console.log("User is logged in with email " + user.email)
        this.authenticated = true
        this.userEmail = user.email
        if (this.$route.name === 'login')
          this.$router.push({name: 'home'}).catch(err => console.log(err))
      }
      else {
        console.log("User is not logged in")
        this.authenticated = false
        if (this.$route.name !== 'login')
          this.$router.push({name: 'login'}).catch(err => console.log(err))
      }
    });
  }
}
</script>

<style lang="scss">



#title {
margin-left: 10%;
margin-bottom: 10%;
color: rgb(0, 0, 0);
font-size: 25px;
font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}


.navbtns{
text-align: center;
}
.nvb{
font-size: 20px;
font-weight: bold;
}

.logout{
color: red;
margin-left: 10%;
}

</style>
