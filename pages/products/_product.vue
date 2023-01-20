<template>
  <main>
    {{ JSON.stringify(data) }}
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
import Products from '../../components/Products.vue'

export default {
  components: {
    Products,
  },
  async asyncData(req) {
    try {
      console.log('hello');
      const data = await Stack.getEntryByUrl({
        contentTypeUid: 'products',
        entryUrl: `${req.route.fullPath}`,
        referenceFieldPath: [
          'page_components.product_list.products',
          'page_components.product_list.products.product_details.sku',
        ],
        jsonRtePath: ['description'],
      })
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
