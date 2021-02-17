<template>
  <spp :blob="blob"></spp>
</template>
<script>
export default {
  head () {
    return {
      title: this.blob.display
    }
  },
  data () {
    return {
      blob: {
        id:"NNplantRich",
        scientific:"",
        common:"Non-native Plant Richness",
        display:"Non-native Plant Richness",
        det:false,
        useavailnorth:false,
        useavailsouth:false,
        coefnorth:true,
        coefsouth:true,
        map:true,
        sectornorth:false,
        sectorsouth:false,
        idprev:"NNplantRich",
        idnext:"NNplantRich",
        taxonid:"nnplants",
        taxonname:"Non-native plant richness"
      }

    }
  }
}
</script>