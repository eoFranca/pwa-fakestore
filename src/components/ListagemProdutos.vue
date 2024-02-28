<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
const produtos = ref([]);

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
    <h1>Produtos</h1>
    <div class="container">
      <div class="card" v-for="(produto,index) in produtos" :key="index">
      
        <h1 class="card--title">{{ produto.title }}</h1>
        <img v-if="produto.imagem" class="card--avatar" :src="produto.image" :alt="produto.title" />
        <button @click="descricao(index) ">Descrição</button>
        <div v-if="produto.lerMais" class="descricao">
          <p>{{ produto.description }}</p>
        </div>
        <p>{{ formatPrice(produto.price) }}</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
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
  height: 25rem;
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