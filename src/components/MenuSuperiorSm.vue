<script setup>
  import { ref } from 'vue';
  import Home from 'vue-material-design-icons/Home.vue';
  import CartPlus from 'vue-material-design-icons/CartPlus.vue';
  import Account from 'vue-material-design-icons/Account.vue';
  import Menu from 'vue-material-design-icons/Menu.vue';

  const menuAberto = ref(false);
</script>

<template>
      <header>
    <img src="@/assets/fish.png" alt="Logo" />
    <h1>FakeStore - Sm</h1>
  </header>
  <div class="footer">
    <CartPlus/>
    <Account/>
    <Home/>
   





































    
  
    <div class="header--icons">
      
      <Menu class="menu-hamburger" @click="menuAberto = !menuAberto" />
    </div>
  </div>

<nav>
    <ul v-if="menuAberto" :class="menuAberto ? 'menu' : ''">
      <li>Home</li>
      <li>Eletrônicos</li>
      <li>Jóias</li>
      <li>Masculino</li>
      <li>Feminino</li>
    </ul>
  </nav>
</template>

<style scoped>
 .footer{
  width: 100%;
  height: 7vh;
  background-color: rgb(219, 217, 217);
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10%;
  position: fixed;
  bottom: 0;
 }
 header {
    background: #fff;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
    padding: 0.2rem 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
  }

  header  img {
    width: 3rem;
    height: 3rem;
    margin-right: 0.5rem;
  }
  nav ul {
    display: flex;
    gap: 1rem;
  }
  nav li {
    list-style: none;
  }
nav .menu {
      display: flex;
      flex-direction: column;
      position: fixed;
      background-color: rgba(255, 255, 255, 0.9);
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
      border-top-left-radius: 10px;
      right: 0;
      bottom: 7vh;
      text-align: left;
      padding: 10px 16px;
    }
    nav .menu li {
      display: block;
      margin-top: 12px;
    }
</style>