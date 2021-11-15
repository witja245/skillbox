<template>
  <div class="col-lg-4 col-md-4 col-sm-6" v-for="(product, index) in products" :key="index">
    <div class="f_p_item">
      <div class="f_p_img">
        <img class="img-fluid" :src="product.image" :alt="product.title">
        <div class="p_icon">
          <a href="#"><i class="lnr lnr-heart"></i></a>
          <a href="#"><i class="lnr lnr-cart"></i></a>
        </div>
      </div>
      <a href="#"><h4>{{ product.title }}</h4></a>
      <h5>{{ product.price }} &#8381;</h5>
    </div>
  </div>
</template>
<script>
export default {
  props: ['products'],
};
</script>
