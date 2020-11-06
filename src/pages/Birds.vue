<template>
  <q-page class="flex">
    <div class="row q-pa-lg">
      <div class="col-12"><h4>{{ blob.name }}</h4></div>
      <div class="col-12" v-for="spp in blob.species" :key="spp.display">
        <a :href="'/' + blob.id + '/'+ spp.id"><div class="text-body1">{{ spp.display }}</div></a>
      </div>
    </div>

  </q-page>
</template>

<script>
const taxon = 'birds'

export default {
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
