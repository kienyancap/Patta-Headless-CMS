<template>
  <main
    v-if="components"
    :data-pageref="entryUid"
    data-contenttype="page"
    :data-locale="locale"
  >
    <ClientOnly>
      <Devtools />
    </ClientOnly>
    <template v-for="(component, index) in components">
      <!-- <HeroBanner
        v-if="component.hero_banner && page === 'Home'"
        :key="'hero_banner' + index"
        title="home-content"
        :data="component.hero_banner"
      /> -->
      <HeroBanner
        v-if="component.hero_banner && page !== 'Products'"
        :key="'products' + index"
        title="product-content"
        :data="component.hero_banner"
      />
      <BlogSection
        v-if="component.from_blog"
        :key="'from_blog' + index"
        :data="component.from_blog"
      />
      <SectionWithCards
        v-if="component.section_with_cards"
        :key="'section_with_cards' + index"
        :data="component.section_with_cards"
      />
      <SectionWithBuckets
        v-if="component.section_with_buckets && page === 'Home'"
        :key="'section_with_buckets' + index"
        :data="component.section_with_buckets"
      />
      <AboutSectionBucket
        v-else-if="component.section_with_buckets && page === 'About Us'"
        :key="'section_with_buckets' + index"
        :data="component.section_with_buckets"
      />
      <TeamSection
        v-if="component.our_team"
        :key="'our_team' + index"
        :data="component.our_team"
      />
      <SectionWithEmbedObject
        v-if="component.section_with_html_code && page === 'Contact Us'"
        :key="'section_with_html_code' + index"
        :data="component.section_with_html_code"
      />
      <SectionWithEmbedObject
        v-if="component.section_with_html_code && page !== 'Contact Us'"
        :key="'section_with_html_code' + index"
        :data="component.section_with_html_code"
      />
      <ProductList
        v-if="component.product_list"
        :key="'product' + index"
        :data="component.product_list"
      />
    </template>
  </main>
</template>

<script lang="ts">
import BlogSection from '../components/BlogSection.vue'
import AboutSectionBucket from '../components/AboutSectionBucket.vue'
import SectionWithBuckets from '../components/SectionWithBuckets.vue'
import SectionWithEmbedObject from '../components/SectionWithEmbedObject.vue'
import TeamSection from '../components/TeamSection.vue'
import SectionWithCards from '../components/SectionWithCards.vue'
import HeroBanner from '../components/HeroBanner.vue'
import ProductList from '../components/ProductList.vue'
import SneakerProducts from '../components/SneakerProducts.vue'
import Devtools from './DevTools.vue'

export default {
  components: {
    HeroBanner,
    SectionWithBuckets,
    AboutSectionBucket,
    SectionWithCards,
    TeamSection,
    BlogSection,
    SectionWithEmbedObject,
    Devtools,
    ProductList,
  },
  props: {
    components: {
      required: true,
      type: Array,
    },
    page: {
      required: true,
      type: String,
    },
    entryUid: {
      required: true,
      type: String,
    },
    locale: {
      required: true,
      type: String,
    },
  },
}
</script>
