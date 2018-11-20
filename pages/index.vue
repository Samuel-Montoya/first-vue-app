<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        your portal
      </h1>
      <h2 class="subtitle">
        welcome to tog
      </h2>
      <div class="links">
        <button 
          class="button--green" 
          @click="handleClick('register')">Create Account</button>
        <button 
          class="button--grey" 
          @click="handleClick('login')">Login</button>
      </div>

      <div v-if="loginType === 'login'">
        <h1 class="title is-3">Login</h1>
        <h2 class="subtitle is-6">enter your username and password</h2>
        <div class="field">
          <p class="control has-icons-left has-icons-right">
            <input 
              v-model="username"
              class="input"
              placeholder="Username"
              @change="checkUsername()">
            <span class="icon is-small is-left">
              <i class="fas fa-user"/>
            </span>
            <span 
              v-if="isValid" 
              class="icon is-small is-right">
              <i 
                class="fas fa-check" 
                style="color: green"/>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control has-icons-left">
            <input 
              class="input" 
              type="password" 
              placeholder="Password">
            <span class="icon is-small is-left">
              <i class="fas fa-lock"/>
            </span>
          </p>
        </div>
        <a 
          class="button is-info" 
          style="width: 100%">Login</a>
      </div>
      <div v-else>
        <h1 class="title is-3">Register</h1>
        <h2 class="subtitle is-6">create your username and password</h2>
        <div class="field">
          <p class="control has-icons-left has-icons-right">
            <input 
              v-model="username"
              class="input"
              placeholder="Username"
              @change="checkUsername()">
            <span class="icon is-small is-left">
              <i class="fas fa-user"/>
            </span>
            <span 
              v-if="isValid" 
              class="icon is-small is-right">
              <i 
                class="fas fa-check" 
                style="color: green"/>
            </span>
          </p>
        </div>
        <div class="field">
          <p class="control has-icons-left">
            <input 
              class="input" 
              type="password" 
              placeholder="Password">
            <span class="icon is-small is-left">
              <i class="fas fa-lock"/>
            </span>
          </p>
        </div>
        <a 
          class="button is-primary" 
          style="width: 100%">Register</a>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  asyncData() {
    return { loginType: 'login', isValid: false }
  },
  components: {
    Logo
  },
  methods: {
    handleClick(mode) {
      this.loginType = mode
    },
    checkUsername() {
      if(this.username.length){
        this.isValid = true
      } else {
        this.isValid = false
      }
    }
  }
};
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 5px;
}

.links {
  padding-top: 5px;
  margin-bottom: 50px;
}
</style>
