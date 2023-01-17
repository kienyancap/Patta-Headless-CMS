<template>
  <div class="product-list-container">
    <h1>{{ data.title }}</h1>
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
          {{ products.title }}
        </h2>
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
  padding: 60px;
  max-width: 1050px;
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
  font-family: f1-black;
  font-size: 62px;
  line-height: 62px;
  margin: 0;
}
</style>
