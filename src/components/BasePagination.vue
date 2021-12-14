<template>
  <div class="right_page ml-auto">
    <nav class="cat_page" aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item"><a class="page-link" href="#">
          <i class="fa fa-long-arrow-left" aria-hidden="true"></i>
        </a></li>
        <li class="page-item " :class="{'active': pageNumber === page }"
            v-for="pageNumber in pages" :key="pageNumber">
          <a class="page-link" href="#" @click.prevent="paginate(pageNumber)">
            {{ pageNumber }}
          </a>
        </li>
        <li class="page-item"><a class="page-link" href="#">
          <i class="fa fa-long-arrow-right" aria-hidden="true"></i>
        </a></li>
      </ul>
    </nav>
  </div>
</template>
<script>
export default {
  model: {
    prop: 'page',
    event: 'paginate',
  },
  props: ['page', 'count', 'perPage'],
  computed: {
    pages() {
      return Math.ceil(this.count / this.perPage);
    },
  },
  methods: {
    paginate(page) {
      this.$emit('paginate', page);
    },
  },
};
</script>
