<script setup>
const route = useRoute();
const { slug } = route.params;
const { locale } = useI18n();

const product = await usePage({ slug, type: "pdp", locale: locale.value });
useOgtags(product);
</script>

<template>
  <RenderPage :data="product">
    <ProductDetail :product="product.commercetoolsProduct" />
    <ProductReviews v-if="product.reviews" :reviews="product.reviews.data" />
  </RenderPage>
</template>
