<template>
  <spp :blob="blob"></spp>
</template>
<script>
const taxon = 'habitats'
import axios from 'axios'
export default {
  head () {
    return {
      title: this.blob.display
    }
  },
  asyncData ({ params }) {
    return axios.get(`https://science.abmi.ca/results/reports/2020/images/${taxon}/${params.id}/index.json`)
    .then((response) => {
      return { 
        blob: response.data
      }
    })
  }
}
</script>