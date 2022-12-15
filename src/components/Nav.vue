<template>
  
  <nav class="">
    <logo/>
    <div  class="burger-menu">
    <img src="https://www.svgrepo.com/show/316704/duotone-menu-hamburger.svg" alt="" @click="showMenu = !showMenu" >
    
    </div>
    

    <ul class="link-burger" :class="showMenu? `burger-menu-show` : `main-menu`" v-if="showMenu"  >
        
        <li>
          <router-link to="/">Task Manager</router-link>
        </li>

        <li>
          <router-link to="/account">Your Account</router-link>
        </li>
        
        <li>
          <button @click="signOut" class="button-logOut">Log out</button>
        </li>
    </ul>
    <ul  class="showMenu">
       
        <li class="links">
          <router-link to="/" >Task Manager</router-link>
        </li>
        <li  class="links">
          <router-link to="/account">Your Account</router-link>
        </li>
        <li>
          <button @click="signOut" class="button" >Log out</button>
        </li>
    
    </ul>

    
  
  </nav>
</template>


<script setup>
import PersonalRouter from "./PersonalRouter.vue";
import { useUserStore } from "../stores/user";
import { computed } from "vue";
import { useRouter } from "vue-router";
import { ref } from 'vue';
import Logo from '../components/Logo.vue'

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

const signOut = async () => {
  try{
    await useUserStore().signOut();
      // redirects user to the homeView
      redirect.push({ path: "/auth/login" });
  
  } catch (error) {
    console.log(" error log out");
  }
  return
  errorMsg.value = "error";
};


const showMenu = ref(false)

</script>

<style>


 .burger-menu{
    display: none;
  }

  .burger-menu-show{
    display:none
  }

.showMenu{
  display: flex;
  justify-content:flex-end;
  align-items: center;
  width: 100%;
  margin-right: 3rem;
}

@media (max-width: 767px) {
 
 nav{

  flex-direction: column;
 }
.burger-menu{
  display:flex
}

  .burger-menu-show{
   
    display: flex;
    flex-direction: column;
    align-items:center;
    width: 100%;
 
  }

  .showMenu{
 display: none;
}

.link-burger li{
  margin: 0.5rem
}

}



</style>
