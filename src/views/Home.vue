<template>
  <div class="home-content">
    <div class="col-md-2">
    <h3>Categorías</h3><br>
    Figuras decorativas
    </div>
    <div class="col-md-10 list-target-products">
      <ProductTarget v-for="(info, index) in products" :key="index" :product=info ></ProductTarget>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'
import ProductTarget from '@/components/ProductTarget.vue'

const axiosInstance = axios.create({
  headers: {
    "Access-Control-Allow-Origin": "*"
  }
});


export default {
  name: 'Home',
  components: {
    ProductTarget
  },
  data () {
    return {
      products:[]
    }
  },
  created: function() {
    axiosInstance.post('https://7ed8-2800-484-5181-98e0-c0c6-3d11-1df-9179.ngrok.io', {
      query: `{
        getProduct {
          name
          description
          stock
          range
          img_info
        }
      }`
    })
    .then( response => {
      console.log(response.data.data.getProduct);
      this.products = response.data.data.getProduct;
    })
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