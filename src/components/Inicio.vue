<template>
  <div>
<div class="nav-inicio">
     <Logo/>
     <div class="">

        <RouterLink to="/auth/login" class="sign in">sign in</RouterLink>
        <RouterLink to="/auth/signup" class="sign up">Free trial</RouterLink>
    </div>
</div>
 <div class="organize">
       <h1> Organize your work and your life</h1>
        <p>Stay focused, get organized and bring calm to your life with ToDoList.</p>
        <RouterLink to="/auth/signup" class="sign up">Free trial</RouterLink>

</div>

<div class="organize">
       <h1>A simple and powerful task management</h1>
    <div class="task-management">
        <div class="cart">
            <img src="https://media.istockphoto.com/id/516040670/vector/set-realistic-monitors-laptop-tablet.jpg?s=612x612&w=0&k=20&c=XCE7VZVz0OT5apWYJp0OAX2wrhFIwL0ZUT596nrT--8=" alt="multi-device">
            <h2>With you everywhere</h2>
            <p>Use the application on any device</p>
        </div>
        <div class="cart">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ75Y4WsDZuMgP_LyU1HHvnk_sqAfH2AgyR4Q&usqp=CAU" alt="">
            <h2>Productivity methods</h2>
            <p>Productivity recommendations</p>
        </div>
        <div class="cart">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRRudqVM8tv9iMt18DRZGGE7n2ZLPxrud2YiA&usqp=CAU" alt="">
            <h2>Give your style</h2>
            <p>Customize your task lists with filters</p>
        </div>


    </div>
</div>


  </div>
</template>

<script setup>
import Logo from './Logo.vue'
import { useRouter, RouterLink } from "vue-router";




</script>

<style>
.nav-inicio{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0rem 3rem 0rem 1rem;
   
}

.sign{
    padding: 1rem 2rem;
    border-radius: 10%;
    margin:0rem 1rem
}  

.up{
    background-color: #65083d;
    color: white;
}
.up:hover {
    background-color: #ad156b;
}

.in{
    color:rgb(108, 106, 106)
}
.in:hover{
    background-color:rgb(225, 221, 221) ;
}
.organize{
    display: flex;
    flex-direction: column;
    align-content: center;
    align-items: center;
    margin:2rem 0rem;
    

}
.cart{
    margin:2rem 4rem;
    
}



.task-management{
    display: flex;
    align-content: center;
   align-items: center;
}


</style>