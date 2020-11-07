<template>
  <div>
    <v-row>
      <v-col offset-md="1">
        <div class="text-h4">{{ blob.name }}</div>
      </v-col>
    </v-row>
    <v-row>
      <v-col offset-md="1">
        <div v-for="spp in blob.species" :key="spp.display">
          <a :href="'/' + blob.id + '/'+ spp.id">
            <div class="text-body1">
              {{ spp.display }}
            </div>
          </a>
        </div>
      </v-col>
    </v-row>
  </div>
</template>
<script>
export default {
  name: 'Toc',
  props: ['blob']
}
</script>
