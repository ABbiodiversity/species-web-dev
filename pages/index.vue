<template>
  <div>
    <h1 class="title">{{ title }}</h1>
    <p>This is the development version of the species website by the ABMI Science Centre.</p>
    <ul>
      <li><a href="/mammals-camera/">Mammals (Camera)</a></li>
      <li><a href="/birds/">Birds</a></li>
      <li><a href="/mites/">Mites</a></li>
      <li><a href="/vplants/">Vascular Plants</a></li>
      <li><a href="/mosses/">Mosses</a></li>
      <li><a href="/lichens/">Lichens</a></li>
    </ul>
  </div>
</template>
<script>
import axios from 'axios'
const group = 'birds';

export default {

  data () {
    return {
      title: 'Species Results'
    }
  },
  head () {
    return {
      title: this.title,
    }
  }

}
</script>
