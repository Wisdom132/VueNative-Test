<template>
  <view class="container">
    <text class="text-color-dark header">{{login}}</text>
    <text-input
      placeholder="Your Email"
      :style="{height: 35, width: 300, borderColor: 'black', borderWidth: 1,borderRadius:22,padding:10}"
      v-model="loginDetails.email"
    />

    <text-input
      type="number"
      placeholder="Your Password"
      :style="{height: 35, width: 300, borderColor: 'black', borderWidth: 1,marginTop:30,marginBottom:20,borderRadius:22,padding:10}"
      v-model="loginDetails.password"
    />

    <button
      class="btn"
      @press="onPressLearnMore"
      title="Submit"
      color="#0d5fb5"
      accessibility-label="Learn more about this blue button"
    />
  </view>
</template>
<script>
export default {
  // props: {
  //   navigation: {
  //     type: Object
  //   }
  // },
  data() {
    return {
      loginDetails: {
        email: "",
        password: ""
      },
      login: "Login"
    };
  },
  methods: {
    getPostTitle() {
      fetch("https://jsonplaceholder.typicode.com/posts")
        .then(response => response.json())
        .then(json => {
          this.posts = json.splice(0, 12);
          console.log(this.posts);
        });
    },
    onPressLearnMore() {
      alert(
        `Your email is ${this.loginDetails.email} and your password is ${this.loginDetails.password}`
      );
    }
  },
  created() {
    this.getPostTitle();
  }
};
</script>

<style>
.btn {
  margin-top: 50px;
}
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
.header {
  font-weight: 700;
  font-size: 40px;
  padding-bottom: 20px;
}
</style>
