<!-- COMPONENTE BOILERPLATE -->
 
  <template>
    <div>
 
 <Header/>
  <div class="container">
    <h3>Sign in</h3>
    <form @submit.prevent="signIn" class="form-sign-in">
        <div id="user-email">
          <label for="email"><span>Email</span></label>
          <input
            type="email"
            autocomplete="off"
            id="email"
            v-model="email"
          />
        </div>
        <div id="user-password">
          <label for="password">Password</label>
          <input
            type="password"
            autocomplete="off"
            id="password"
            v-model="password"
          />
        </div>
        <button class="button" type="submit">Sign in</button>
        </form>
  
  
   <p>Dont have an account? <PersonalRouter :route="route" :buttonText="buttonText" class="sign-up-link"/></p>
  </div>
</div>
</template>

<script setup>
import Header from "./Header.vue"
import PersonalRouter from "./PersonalRouter.vue";
import { ref } from "vue"
import { useRouter } from "vue-router";
import { useUserStore } from "../stores/user";
// Route Variables
const route = "/auth/signup";
const buttonText = "Sign Up";


const errorMsg = ref("");
const email = ref("");
const password = ref("")
const redirect = useRouter()

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
      }, 5000);
       console.log(" error ingreso");
      }
  return
    errorMsg.value = "error";
  }
</script>

<style>
.container {
  display:flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;

}

.form-sign-in{
  display: flex;
  flex-direction: column;

}
.form-sign-in div{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 1rem;
}



</style>
