<template>
  <div class="product-list-container">
    <template v-for="(products, index) in data.products">
      <NuxtLink
        :key="index"
        class="product-list-item"
        :to="products.url"
      >
        <img 
          class="product-list-img"
          :src="products.product_details.image.url"
          alt="products.product_details.image.title"
        />
        <h2 class="product-name">
          {{ products.product_details.image }}
        </h2>
        <p>{{ products.product_details.image }}</p>
      </NuxtLink>
    </template>
  </div>
</template>

<script>
export default {
  props: ['data'],  
}
</script>

<style scoped>
.product-list-container {
  background: #fff;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
}

.product-list-item {
  display: flex;
  align-items: stretch;
  justify-content: stretch;
  width: 50%;
  align-items: center;
  overflow: hidden;
}

.product-name {
  width: 100%;
  display: block;
}

h1 {
  flex-basis: 100%;
  font-size: 62px;
  line-height: 62px;
  margin: 0;
}
</style>
