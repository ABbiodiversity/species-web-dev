<template>
  <div>
    <h1 class="title">{{ title }}</h1>
    <ul>
      <li v-for="spp in blob">
        <a v-bind:href="'/' + group + '/'+ spp.SpeciesID">{{ spp.DisplayName }}</a>
        </li>
    </ul>
  </div>
</template>
<script>
const group = 'mites'
const Group = 'Soil Mites'
import axios from 'axios'

export default {

  data () {
    return {
      title: 'Species Results for ' + Group,
      group: group
    }
  },
  head () {
    return {
      title: this.title,
    }
  },
  asyncData () {
    return axios.get(`http://sc-dev.abmi.ca/reports/2018/api/${group}/index.json`)
    .then((res) => {
      return { 
        blob: res.data
      }
    })
    .catch((e) => {
      error({ statusCode: 404, message: 'Data not found' })
    })
  }

}
</script>
