<template>
  <div>
   <RouterLink to='/inicio'> <Logo/></RouterLink>
   <div class="container-log">
  
  
    <div class="container-form">

    <div class="form-title">
      
        <h3 class="title-inicio">Sign up</h3>
        
        
    </div>

    <form @submit.prevent="signUp" class="form-sign-in">
      <div class="form">
        <div class="form-input">
          <label class="input-field-label">E-mail</label>
          <input
            type="email"
            class="input-field"
            placeholder="example@gmail.com"
            id="email"
            v-model="email"
            required
          />
        </div>
        <div class="form-input">
          <label class="input-field-label">Password</label>
          <input
            type="password"
            class="input-field"
            placeholder="**********"
            id="password"
            v-model="password"
            required
          />
        </div>
        <div class="form-input">
          <label class="input-field-label">Confirm password</label>
          <input
            type="password"
            class="input-field"
            placeholder="**********"
            id="confirmPassword"
            v-model="confirmPassword"
            required
          />
        </div>
        <button class="button button-sign up" type="submit">Sign Up</button>
        <p class="acount-p">
          Have an account?
          <PersonalRouter
            :route="route"
            :buttonText="buttonText"
            class="sign-up-link"
          />
        </p>
      </div>
    </form>

    <div v-show="errorMsg">{{errorMsg}}</div>
  </div>
 

  <div class="form-title"><img class="trello-img" src="https://blog.trello.com/hs-fs/Trello-Like-a-Pro-final.png"  alt="">

  <p class="start">Start organizing your tasks!</p>
</div>
 </div>

</div>
</template>

<script setup>
import { ref, computed } from "vue";
import PersonalRouter from "./PersonalRouter.vue";
import { supabase } from "../supabase";
import { useRouter } from "vue-router";
import { useUserStore } from "../stores/user";
import { storeToRefs } from "pinia";

import Logo from "./Logo.vue"

// Route Variables
const route = "/auth/login";
const buttonText = "Sign In";

// Input Fields
const email = ref("");
const password = ref("");
const confirmPassword = ref("");

// Error Message
const errorMsg = ref("");

// Router to push user once SignedUp to Log In
const redirect = useRouter();

// Arrow function to SignUp user to supaBase with a timeOut() method for showing the error
const signUp = async () => {
  if (password.value === confirmPassword.value) {
    try {
      // calls the user store and send the users info to backend to logIn
      await useUserStore().signUp(email.value, password.value);
      // redirects user to the homeView
      redirect.push({ path: "/auth/login" });
    } catch (error) {
      // displays error message
      errorMsg.value = error.message;
      // hides error message
      setTimeout(() => {
        errorMsg.value = null;
      }, 5000);
    }
    return;
  }
  errorMsg.value = "error";
};
</script>

<style>


@media (max-width: 760px) {

.container-log{
  flex-direction: column;
  align-items: center;
  
  
}
.container-form{
  width:100%;
  
}
.trello-img{
  max-width: 100%;
  max-height: 100%;
  margin-bottom: 1rem;

}
.img-sig-in{
  width: 100%;
}
}
</style>
