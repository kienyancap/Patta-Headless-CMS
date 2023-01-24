<template>
  <!-- <div class="product-wrapper"> -->
  <div class="blog-container">
    <div class="blog-column-left">
      <section class="product-section">
        <div class="product-img-wrapper">
          <img
            :src="data.product_details.image.url"
            class="product-img"
            :alt="data.product_details.image.title"
          />
        </div>
      </section>
    </div>
    <div class="product-description">
      <h1 class="product-title">{{ data.title }}</h1>
      <h2>Description</h2>
      <div v-html="data.description" />
       <p>Rating: {{ data.custom }}</p>
      <h4>SKU: {{ data.product_details.sku[0].sku }}</h4>     
    </div>
  </div>

  <!-- </div> -->
</template>

<script>
export default {
  props: ['data'],
}
</script>

<style scoped>
.product-description {
  padding: 0 60px 60px;
}

.product-img-wrapper {
  max-width: 100%;
  overflow: hidden;
}

.product-img {
  max-width: 100%;
}

.product-section {
  display: flex;
  max-width: 100%;
  flex-direction: column;
  font-family: f1-regular;
}

/* .product-title {
  font-family: f1-bold;
  font-size: 4.2rem;
  line-height: 1.142;
  display: inline-block;
  margin: 0;
  background-color: red;
}

.product-title {
  font-size: 2.5rem;
  margin-left: 1rem;
  font-family: f1-regular;
}

.product-biography {
  max-width: 100%;
}

.product-wrapper {
  max-width: 1050px;
  background: #fff;
  margin: 0 auto;
} */
</style>