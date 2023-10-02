<template>
  <div>
    <h1>Lista de Produtos</h1>
    <ul>
      <li v-for="product in products" :key="product.id">
        <div>
          <img :src="product.image" :alt="product.title" width="100" height="100">
        </div>
        <div>
          <h2>{{ product.title }}</h2>
          <p>Preço: $ {{ product.price }}</p>
          <p>{{ product.description }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      products: []
    };
  },
  mounted() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await this.$http.get('https://fakestoreapi.com/products');
        this.products = response.data;
      } catch (error) {
        console.error('Erro ao buscar a lista de produtos:', error);
      }
    }
  }
};
</script>

<style scoped>
/* Estilos CSS personalizados para a sua lista de produtos */
</style>
