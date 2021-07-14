<template>
  <div>
    <div v-if="authState !== 'signedin'">You are signed out.</div>
    <amplify-authenticator>
      <div v-if="authState === 'signedin' && user">
        <div>Hello, {{ user.username }}</div>
      </div>
      <amplify-sign-out></amplify-sign-out>
    </amplify-authenticator>
  </div>
</template>

<script>
export default {
  name: "logout",
  created() {
    this.user = JSON.parse(localStorage.user ? localStorage.user : "");
    this.authState = localStorage.authState;
  },
  data() {
    return {
      user: undefined,
      authState: undefined,
      unsubscribeAuth: undefined
    };
  },
  beforeDestroy() {
    this.unsubscribeAuth();
  }
};
</script>

<style lang="scss" scoped></style>
