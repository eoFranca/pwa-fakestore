<script setup>
import { useScreen } from '@/composables/MobileMenu';
import { ref, onMounted } from 'vue';
import axios from 'axios';
const produtos = ref([]);


const { browserWidth, deviceWidth, isMobile, isDesktop } = useScreen();

onMounted(async () => {
  const response = await axios.get('https://fakestoreapi.com/products');
  produtos.value = response.data;
});

const formatPrice = (price) => `R$ ${price.toFixed(2).replace('.', ',')}`;
let lerMais = ref(false);
let imagem = ref(true);
function descricao (index){

  produtos.value[index].lerMais = !produtos.value[index].lerMais;
  produtos.value[index].imagem = !produtos.value[index].lerMais;
}
</script>


<template>
  <div>
    <h1>
       Produtos - {{ browserWidth }} - {{ deviceWidth }} - {{
      isMobile}} 
      <span v-if="isMobile">É móvel</span>
    </h1>
    <div class="container">
      <div class="card" v-for="(produto,index) in produtos" :key="index">
      
        <h1 class="card--title">{{ produto.title }}</h1>
        <img v-if="produto.imagem" class="card--avatar" :src="produto.image" :alt="produto.title" />
        <button class="b-descricao" @click="descricao(index) ">Descrição</button>
        <div v-if="produto.lerMais" class="descricao">
          <p>{{ produto.description }}</p>
        </div>
        <p>{{ formatPrice(produto.price) }}</p>
      </div>
    </div>
  </div>
  <div v-if="isDesktop" class="footer">
    <h2>Footer</h2>
  </div>

</template>
<style scoped>

.footer{
  width: 100%;
  height: 10vh;
  background-color: #222;
  display: flex;
  justify-content: center;
  color: #fff;

}
.b-descricao{
  background-color: transparent;
   padding: 5px;
   border: solid 1px gray;
   border-radius: 9%;
   transition: all 0.5s;
   
}
.b-descricao:hover{
  background-color: #22222228;
}
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
  align-items: center;
  margin: auto;
  padding: 1rem 0;
  
}
.card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
  width: 15rem;
  height: 30rem;
  background: #fff;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  border-radius: 10px;
  margin: auto;
  overflow: hidden;
}
.card--avatar {
  width: 50%;
  height: auto;
  object-fit: cover;
  margin-bottom: 0.5rem;
}
.card--avatar img
  { max-height: 20px;}
   
.card--title {
  color: #222;
  font-weight: 700;
  text-transform: capitalize;
  font-size: 1.1rem;
  margin-top: 0.5rem;
}

@media (max-width: 768px) {
  .container {
    gap: 0.5rem;
  }
  .card {
    width: 92%;
  }
}

@media (min-width: 768px) and (max-width: 1024px) {
  .card {
    width: 22rem;
  }
}
</style>