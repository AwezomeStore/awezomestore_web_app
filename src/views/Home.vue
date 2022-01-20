<template>
  <div class="home-content">
    <div class="col-md-2">
      <button @click="superTest">MUAJAJJ</button>
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

export default {
  name: 'Home',
  components: {
    ProductTarget
  },
  data () {
    return {
      products:[
        {rating: 4.235,
        title: "michi1"},
        {rating: 2.235,
        title: "michi2"},
        {rating: 3.235,
        title: "michi3"},
        {rating: 5.235,
        title: "michi4"},
        {rating: 2.235,
        title: "michi5"},
        {rating: 1.235,
        title: "michi6"},
        {rating: 0.235,
        title: "michi7"}
      ]
    }
  },

  methods: {
    async superTest () {
      const res = await axios.post('http://localhost:4010/api', {
        query: `{
          getUser {
            id
          }
        }`
      })
      console.log(res.data.data);
    },
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