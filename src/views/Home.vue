<template>
  <div class="home-content">
    <div class="col-md-2">
    Component of sections
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
    axiosInstance.post('http://localhost:4010/api', {
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