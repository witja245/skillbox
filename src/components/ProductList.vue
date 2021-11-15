<template>
  <div class="latest_product_inner row">
    <ProductItem :products="products"/>
  </div>
</template>
<script>
import ProductItem from './ProductItem.vue';

export default {
  props: ['products'],
  components: { ProductItem },

};
</script>
