<template>
  <div id="app">
    <amplify-authenticator v-if="authState !== 'signedin'">
      <amplify-sign-in
        header-text="Devhub Sign"
        slot="sign-in"
        @handle-submit="handleSubmit"
      ></amplify-sign-in>
    </amplify-authenticator>
    <router-view v-if="authState === 'signedin' && user"></router-view>
  </div>
</template>
<script>
import { onAuthUIStateChange } from "@aws-amplify/ui-components";

export default {
  name: "app",
  data() {
    return {
      user: undefined,
      authState: undefined
    };
  },
  created() {
    this.unsubscribeAuth = onAuthUIStateChange((authState, authData) => {
      this.authState = authState;
      localStorage.authState = authState;
      this.user = authData;
      localStorage.user = JSON.stringify(authData);
    });
  },
  mounted() {},
  methods: {
    handleSubmit() {
      console.log(1111);
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
