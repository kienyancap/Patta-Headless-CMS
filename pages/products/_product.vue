<template>
  <main>
    <div
      class="product-container"
      :data-pageref="data.uid"
      data-contenttype="products"
      :data-locale="data.locale"
    >
      <div class="product-detail">
        <Products :data="data" />
      </div>
    </div>
  </main>
</template>

<script>
import Stack from '../../plugins/contentstack'
import SneakerProducts from '../../components/SneakerProducts.vue'

export default {
  components: {
    SneakerProducts,
  },
  async asyncData(req) {
    try {
      const data = await Stack.getEntryByUrl({
        contentTypeUid: 'products',
        entryUrl: `${req.route.fullPath}`,
        referenceFieldPath: [
          'page_components.sku',
          'page_components.products',
          'page_components.products.product_details.image'
        ],
        jsonRtePath: ['description'],
      })
      console.log('hallo', data);
      return {
        data: data[0],
      }
    } catch (e) {
      return false
    }
  },
  head(req) {
    return {
      title: req.data.title,
      meta: [
        {
          title: req.data.seo.meta_title,
          name: req.data.seo.meta_title,
          description: req.data.seo.meta_description,
          keywords: req.data.seo.keywords,
        },
      ],
    }
  },
}
</script>
