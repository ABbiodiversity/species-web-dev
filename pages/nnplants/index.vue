<template>
  <toc :blob="blob"></toc>
</template>
<script>
const taxon = 'nnplants'
export default {
  head () {
    return {
      title: this.blob.name
    }
  },
  data () {
    return {
      blob: {}
    }
  },
  mounted () {
    this.$axios
      .get('https://science.abmi.ca/results/reports/2020/images/' + taxon + '/index.json')
      .then((response) => {
        this.blob = response.data
      })
  }
}
</script>
