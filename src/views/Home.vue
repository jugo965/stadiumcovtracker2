<template>
  <div id="appstyle">
    <div class="home">
  <div class="row">
    <img class="stadion" src="../assets/stadion.jpg">
  </div>
  <div class="row">
  <a class="hometxt">Welcome to <b>StadiumCOVtracker</b>. Please</a><router-link to="/Login">&nbsp;Login</router-link><a>&nbsp;or</a><router-link to="/Register">&nbsp;Register</router-link><a>&nbsp;to use this app.</a>
</div>
</div>
</div>
</template>

<script>


export default {

 
  name: "home",
};
</script>

<style>
#appstyle{
padding-top:50px;
padding-left:50px;
}
.home{
  margin-left: 18%;
}
.hometxt{
  margin-left:6%;
}
.stadion{
  width:700px;
  height:400px;
}
</style>