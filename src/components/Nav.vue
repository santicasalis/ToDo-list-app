<template>
  <nav>
    <!-- <PersonalRouter :route="route" :buttonText="buttonText" class="logo-link"/> -->
    <router-link to="/">
      <Logo/>
    </router-link>
    <div>
    <ul class="links">
        <li>
          <router-link to="/">Task Manager</router-link>
        </li>

        <li>
          <router-link to="/account">Your Account</router-link>
        </li>
    </ul>
</div> 
    <div>
      <ul>
        <li class="log-out-welcome">
          <p>Welcome, {{userEmail}}</p>
        </li>
        <li>
          <button @click="signOut" class="button">Log out</button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
// import PersonalRouter from "./PersonalRouter.vue";
import { useUserStore } from "../stores/user";
import { computed } from "vue";
import { useRouter } from "vue-router";
import { ref } from 'vue';
import Logo from "./Logo.vue"
import { supabase } from "../supabase";

//constant to save a variable that will hold the use router method
const route = "/";
const buttonText = "Todo app";

// constant to save a variable that will get the user from store with a computed function imported from vue
// const getUser = computed(() => useUserStore().user);
const getUser = useUserStore().user;

// constant that calls user email from the useUSerStore
const userEmail = getUser.email;

// async function that calls the signOut method from the useUserStore and pushes the user back to the Auth view.
const redirect = useRouter();
const errorMsg = ref("")

const signOut = async () => {
  try {
      // call the user store and send the users info to backend to signOut
      await useUserStore().signOut();
      // redirects user to the homeView
      redirect.push({ path: "/auth/login" });
    } catch (error) {
     
      
       console.log(" error log out");
      }
  return
    errorMsg.value = "error";
  }

</script>


