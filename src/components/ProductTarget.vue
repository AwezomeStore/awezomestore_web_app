<template>
  <div class="col-md-6 col-lg-4 col-xl-3 product-card-container">
  <b-card title="Title" img-src="https://placekitten.com/g/300/450" img-alt="Image" img-top
    class="product-card">
    <b-card-text>
      This is a wider card with supporting text below as a natural lead-in to additional content.
      This content is a little bit longer.
    </b-card-text>
    <div class="rating-product">
      <b-form-rating v-model="value" readonly></b-form-rating>
      <p class="rating-info">{{ product.rating.toFixed(1) }}</p>
    </div>
  </b-card>
  </div>
</template>

<script>
export default {
  name: 'ProductTarget',
  props: {
    product: Object
  }
}
</script>

<style>
.product-card-container {
  padding: .3rem;
}

.product-card-container .product-card{
  background-color: var(--gray-1);
  padding: .5rem;
}

.product-card .card-img-top {
  width: auto;
  margin: auto;
  max-width: 100%;

  max-height: 20rem;
}

.product-card .card-body {
  padding: 1rem .5rem;
}

.rating-product {
  display: flex;
}

.rating-product .b-rating {
  padding: 0rem;
  background-color: transparent;
  border: none;
  width: 50%;
}

.b-rating  .b-rating-icon {
  color: var(--blue-1);
}

.rating-info {
  margin: .5rem;
}

</style>