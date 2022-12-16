<template>
  <div>
  <Nav/>
  <div class="container-profile">
  <div class="img-name">
  <h1>{{username}}</h1>
  <img class="img-profile" :src="avatar_url ? avatar_url : 'https://cdn.pixabay.com/photo/2015/10/05/22/37/blank-profile-picture-973460__480.png'" alt="Profile picture">
  <div>
   
  <input
            type="file"
            name="photo"
           accept=".jpg,.png,.svg "
            />
        </div>
</div>
  <form @submit.prevent="" class="form-sign-in">
        <div id="profile-name" class="form-input">
          <label class="label-font  "  for="name"><span>Name</span></label>
          <input
            type="text"
            autocomplete="off"
            id="name"
           v-model="username"
          />
        </div>
        <div id="profile-surname" class="form-input">
          <label class="label-font " for="surname">Surname</label>
          <input
            type="text"
            autocomplete="off"
            id="surname"
            v-model="password"
          />
        </div>
        <div id="profile-birth" class="form-input">
          <label class="label-font" for="birth">Date of birth</label>
          <input
            type="date"
            autocomplete="off"
            id="birth"
            v-model="password"
          />
        </div>
        <button class="button button-sign up" type="submit">Save</button>
      </form>

  </div>
  <Footer/>
</div>
</template>

<script setup>
  import { supabase } from '../supabase'
  import { onMounted, ref, toRefs } from 'vue'
 import { useUserStore } from "../stores/user";
 import Nav from '../components/Nav.vue'
  import Footer from '../components/Footer.vue'
  

  const userStore = useUserStore();

  const loading = ref(false);
  const username = ref(null);
  const website = ref(null);
  const avatar_url = ref(null);

  onMounted(() => {
    getProfile();
  });

  async function getProfile() {
    await userStore.fetchUser();
    username.value = userStore.profile.username;
    avatar_url.value = userStore.profile.avatar_url;
  }

 
</script>

<style>
.img-profile{
  width: 150px;
  height: 150px;
}

.container-profile{
  display: flex;
  justify-content: space-around;
  margin:4rem 2rem;
  height: 80vh;
  
}
.img-name input {
    margin-top: 15px;
  }
@media (max-width: 760px) {
  .container-profile{
    flex-direction: column;
    align-items: center;
    margin:4rem 1rem
  }
  .img-name{
    display: flex;
    flex-direction: column;
    align-items: center;
  }

}

</style>