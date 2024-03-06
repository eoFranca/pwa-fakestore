<script setup>
import CartPlus from 'vue-material-design-icons/CartPlus.vue';
import Account from 'vue-material-design-icons/Account.vue';
import Menu from 'vue-material-design-icons/Menu.vue';
import Home from 'vue-material-design-icons/Home.vue';
import { useScreen } from '@/composables/MobileMenu';
const { browserWidth, deviceWidth, isMobile } = useScreen();

</script>
<template>
<div v-if="isMobile" class="footer-mobile">
    <CartPlus/>
    <Account/>
    <Home/>
    <Menu/>
    </div>
</template>
<style>
.footer-mobile{
width: 100%;
height: 50px;
background-color: rgb(43, 148, 151);
display: flex;
justify-content: center;
align-items: center;
gap: 10%;
position: fixed;
bottom: 0;
}
</style>