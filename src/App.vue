<template>
  <section class="cat_product_area p_120">
    <div class="container">
      <div class="row flex-row-reverse">
        <div class="col-lg-9">
          <div class="product_top_bar">
            <div class="left_dorp">
              <select class="sorting">
                <option value="1">Default sorting</option>
                <option value="2">Default sorting 01</option>
                <option value="4">Default sorting 02</option>
              </select>
              <select class="show">
                <option value="1">Show 12</option>
                <option value="2">Show 14</option>
                <option value="4">Show 16</option>
              </select>
            </div>
            <BasePagination v-model="page" :count="countProducts" :per-page="productsPerPage" />
          </div>
          <ProductList :products="products"/>
        </div>
        <div class="col-lg-3">
          <ProductFilter></ProductFilter>
        </div>
      </div>
    </div>
  </section>

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
      page: 1,
      productsPerPage: 3,
    };
  },
  computed: {
    filteredProducts() {
      let filteredProducts = products;

      if (this.filterPriceForm > 0) {
        filteredProducts = filteredProducts.filter(product => product.price > this.filterPriceForm);
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
