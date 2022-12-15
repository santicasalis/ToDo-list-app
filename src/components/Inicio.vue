<template>
  <div>
<div class="nav-inicio">
     <Logo/>
     <div class="signs">

        <RouterLink to="/auth/login" class="sign in">Log in</RouterLink>
        <RouterLink to="/auth/signup" class="sign  sign-none">Free trial</RouterLink>
    </div>
</div>
<div class="organize-container">
      <div class="organize">
         <div class="title-inicio"> Organize your work <br/>and your life</div>
         <p>Stay focused, get organized and bring calm to your life with ToDoList.</p>
         <RouterLink to="/auth/signup" class="sign up organize-button">Free trial</RouterLink>
      </div>
      <div class="organize-img"><img src="https://evolbit.net/blog/wp-content/uploads/2018/11/notes-1089x730.jpg" alt="Organize">
    </div>

</div>
<div class="task-management-container">
       <h2 class="title-inicio">A simple and powerful <br/>task management</h2>
    <div class="task-management">
        <div class="cart">
            <img src="data:image/jpeg;base64,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" alt="multi-device">
            <h3>With you everywhere</h3>
            <p>Use the application on any device</p>
        </div>
        <div class="cart">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ75Y4WsDZuMgP_LyU1HHvnk_sqAfH2AgyR4Q&usqp=CAU" alt="">
            <h3>Productivity methods</h3>
            <p>Productivity recommendations</p>
        </div>
        <div class="cart">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRRudqVM8tv9iMt18DRZGGE7n2ZLPxrud2YiA&usqp=CAU" alt="">
            <h3>Give your style</h3>
            <p>Customize your task lists with filters</p>
        </div>


    </div>
</div>

<Footer/>
  </div>
</template>

<script setup>
import Logo from './Logo.vue'
import Footer from './Footer.vue'
import { useRouter, RouterLink } from "vue-router";




</script>

<style>
   @media (max-width: 760px) {
    .nav-inicio{
        flex-direction: column;
    }
    .signs{
        margin-top: 1rem;
    }
    .organize-container{
        display: flex;
        flex-direction: column;
   justify-content: center;
        
    }

    .organize-img { 
      
       display: flex;
       justify-content: center;
    }
   
    .title-inicio{ 
        margin:0rem 1rem
}

.task-management{
    flex-direction: column;
   align-items: center;
}
.cart p{
    margin: 0 1rem;
}
   }
@media (max-width: 350px) {
   .sign-none{
    display: none;
   }
   .in{
    background-color: #65083d;
  color: white;
    
   
}
.in:hover{
    color:#65083d
}

}

</style>