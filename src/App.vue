<template>
  <div class="content__catalog">
    <ProductFilter :price-form.sync="filterPriceForm"
                   :price-to.sync="filterPriceTo"
                   :category-id.sync="filterCategoryId"
                   :color-id.sync="filterColorId">
    </ProductFilter>
    <section class="catalog">
      <ProductList :products="products"/>
      <BasePagination v-model="page" :count="countProducts" :per-page="productsPerPage" />
    </section>
  </div>
</template>

<script>

import products from './data/products';
import ProductList from './components/ProductList.vue';
import BasePagination from './components/BasePagination.vue';
import ProductFilter from './components/ProductFilter.vue';

export default {
  name: 'App',
  components: { ProductFilter, BasePagination, ProductList },
  data() {
    return {
      filterPriceForm: 0,
      filterPriceTo: 0,
      filterCategoryId: 0,
      filterColorId: 0,
      page: 1,
      productsPerPage: 3,
    };
  },
  computed: {
    filteredProducts() {
      let filteredProducts = products;
      if (this.filterPriceForm > 0) {
        filteredProducts = filteredProducts.filter(
          (product) => product.price > this.filterPriceForm,
        );
      }
      if (this.filterPriceTo > 0) {
        filteredProducts = filteredProducts.filter(
          (product) => product.price < this.filterPriceTo,
        );
      }
      if (this.filterCategoryId > 0) {
        filteredProducts = filteredProducts.filter(
          (product) => product.categoryId === this.filterCategoryId,
        );
      }
      if (this.filterColorId > 0) {
        filteredProducts = filteredProducts.filter(
          (product) => product.colorId === this.filterColorId,
        );
      }
      return filteredProducts;
    },
    products() {
      const offset = (this.page - 1) * this.productsPerPage;
      return this.filteredProducts.slice(offset, offset + this.productsPerPage);
    },
    countProducts() {
      return this.filteredProducts.length;
    },
  },
};
</script>
