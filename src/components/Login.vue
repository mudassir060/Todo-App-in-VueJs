<template>
  <div class="container maindiv">
    <h1><strong>Login</strong></h1>
    <br /><br />
    <div class="d-flex">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon1"> Email . . . </span>
      </div>
      <input
        type="text"
        name="email"
        class="form-control"
        placeholder="Enter Email"
        aria-label="Username"
        aria-describedby="basic-addon1"
      />
    </div>
    <br />
    <div class="d-flex">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon1">Password</span>
      </div>
      <input
        type="text"
        name="password"
        class="form-control"
        placeholder="Enter Password"
        aria-label="Username"
        aria-describedby="basic-addon1"
      />
    </div>
    <br />
    <button type="button" class="btn btn-success btn-lg btn-block" @click="login">
      Login
    </button>
  </div>
</template>
<script>
export default {
  name: "Log-in",
  methods:{
      login(){
         console.log("pakistan") 
      }
  }
};
</script>

<style>
.maindiv {
  margin-top: 30%;
}
</style>