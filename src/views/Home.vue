<template>
  <div class="home-content">
    <div class="col-md-2">
    Component of sections
    </div>
    <div class="col-md-10 list-target-products">
      <ProductTarget :product=product></ProductTarget>
      <ProductTarget :product=product></ProductTarget>
      <ProductTarget :product=product></ProductTarget>
      <ProductTarget :product=product></ProductTarget>
      <ProductTarget :product=product></ProductTarget>
      <ProductTarget :product=product></ProductTarget>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import ProductTarget from '@/components/ProductTarget.vue'

export default {
  name: 'Home',
  components: {
    ProductTarget
  },
  data () {
    return {
      product: {rating: 4.235}
    }
  }
}
</script>
<style scoped>
.home-content{
  background: var(--gray-2);
  padding: 1rem 0.5rem;
  display: flex;
}

.list-target-products {
  display: flex;
  flex-wrap: wrap;
}

</style>