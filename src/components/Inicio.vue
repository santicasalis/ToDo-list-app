<template>
  <div>
<div class="nav-inicio">
     <Logo/>
     <div class="">

        <RouterLink to="/auth/login" class="sign in">Log in</RouterLink>
        <RouterLink to="/auth/signup" class="sign up">Free trial</RouterLink>
    </div>
</div>
<div class="organize-container">
      <div class="organize">
         <h1 class="title-inicio"> Organize your work <br/>and your life</h1>
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
            <img src="https://media.istockphoto.com/id/516040670/vector/set-realistic-monitors-laptop-tablet.jpg?s=612x612&w=0&k=20&c=XCE7VZVz0OT5apWYJp0OAX2wrhFIwL0ZUT596nrT--8=" alt="multi-device">
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


  </div>
</template>

<script setup>
import Logo from './Logo.vue'
import { useRouter, RouterLink } from "vue-router";




</script>

<style>

   /* INICIO-WEB */
.nav-inicio{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0rem 3rem 0rem 1rem;
   
}

.sign{
    padding: 1rem 2rem;
    border-radius: 10%;
    margin:0rem 1rem;
    text-decoration: none;
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

/* ORGANIZE */
.organize-container{
display:flex;
align-content: center;

align-items: center;
margin-top: 2rem;
}
.organize{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin:2rem 0rem;
    width: 50%;

}
.organize-img{
    width: 50%;
}
.organize-img img{
 width: 70%;
}
.organize p {
    font-size:1.5rem;
    width: 60%;
    margin:0rem 0rem 2rem 0rem;

    line-height: 40px;
    
}
.organize-button{
  padding: 1.5rem 5rem;
}


.title-inicio{
    font-size: 50px;
    
}


    /* TASK MANAGEMENT */
.task-management-container{
    
    display: flex;
    flex-direction: column;
    align-content: center;
    align-items: center;
    margin:2rem 0rem; 
}
.cart{
    margin:2rem 4rem;
    box-sizing: border-box;
    max-width:20rem;
    max-height: 20rem;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
 
}
.cart h3{
    font-size: 1.5rem;
    text-align: center;
}
.cart p{
    font-size: 20px;
}
.cart img{
   
    object-fit:cover;
}




.task-management{
    display: flex;
    align-content: center;
   align-items: center;
}


</style>