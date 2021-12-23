<template>
  <ProductItem :products="products"/>
</template>
<script>
import ProductItem from './ProductItem.vue';

export default {
  name: 'ProductList',
  props: ['products'],
  components: { ProductItem },

};
</script>
