<template>
  <div>
    <RouterLink to="/inicio" class="router"> <Logo /></RouterLink>

    <div class="container-log">
      <div class="container-form">
        <div class="form-title">
          <h3 class="title-inicio">Sign in</h3>
        </div>

        <form @submit.prevent="signIn" class="form-sign-in">
          <div id="user-email" class="form-input">
            <label class="label-font" for="email"><span>Email</span></label>
            <input type="email" autocomplete="off" id="email" v-model="email" />
          </div>
          <div id="user-password" class="form-input">
            <label class="label-font" for="password">Password</label>
            <input
              type="password"
              autocomplete="off"
              id="password"
              v-model="password"
            />
          </div>
          <button class="button button-sign up" type="submit">Sign in</button>
          <p class="acount-p">
            Dont have an account?
            <PersonalRouter
              :route="route"
              :buttonText="buttonText"
              class="sign-up-link"
            />
          </p>
        </form>
      </div>
      <div class="form-title">
        <img
          class="img-sig-in"
          src="https://images.ctfassets.net/rz1oowkt5gyp/4EdaVcwdrnycEg4bDi0HvB/d02337f14d7596e1d08ffb18b3aaa1e4/Hero-mobile_2x.png?w=540"
          alt="Log in in your task"
        />
      </div>
    </div>
  </div>
</template>
<script setup>
import Swal from "sweetalert2";
import Logo from "./Logo.vue";
import PersonalRouter from "./PersonalRouter.vue";
import { ref } from "vue";
import { useRouter } from "vue-router";
import { useUserStore } from "../stores/user";
// Route Variables
const route = "/auth/signup";
const buttonText = "Sign Up";

const errorMsg = ref("");
const email = ref("");
const password = ref("");
const redirect = useRouter();

// Arrow function to Signin user to supaBase

const signIn = async () => {
  try {
    // calls the user store and send the users info to backend to logIn
    await useUserStore().signIn(email.value, password.value);
    // redirects user to the homeView
    redirect.push({ path: "/" });
  } catch (error) {
    // displays error message
    errorMsg.value = error.message;
    // hides error message
    setTimeout(() => {
      errorMsg.value = null;
    }, 500);
    Swal.fire({
      position: "center",
      icon: "error",
      title: "Your Email and/or password is incorrect",
      showConfirmButton: false,
      timer: 1500,
    });
  }
  return;
  errorMsg.value = "error";
};
</script>
