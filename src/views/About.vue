<template>
  <div class="about">
    <h1>This is an about page</h1>

    <v-btn icon @click="save">
      <v-icon>mdi-check</v-icon>
    </v-btn>

    {{ $store.state.fireUser }}
    <div v-if="!$store.state.fireUser">
      <v-btn color="red" dark @click="singInWithGoogle" block
        ><v-icon left>mdi-google</v-icon>구글로 로그인</v-btn
      >
    </div>

    <div v-else>
      <v-btn color="red" dark @click="signOut" block>
        <v-avatar size="32"
          ><v-img src="$store.state.fireuser.photoURL"></v-img
        ></v-avatar>
        <v-icon left>mdi-google</v-icon>로그아웃</v-btn
      >
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loding: false,
    };
  },
  methods: {
    save() {
      console.log("save");
      this.$firebase.database().ref().child("abcd").set({
        title: "abce",
        text: "cccc",
      });
    },

    async singInWithGoogle() {
      const provider = new this.$firebase.auth.GoogleAuthProvider();
      this.$firebase.auth().languageCode = "ko";
      this.loding = true;
      try {
        const sn = await this.$firebase.auth().signInWithPopup(provider);
        this.store.commit("setFireUser", sn.user);
      } finally {
        this.loding = false;
      }
    },

    signOut() {
      this.$firebase.auth().signOut();
    },
  },
};
</script>

<style></style>
