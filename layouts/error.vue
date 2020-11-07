<template>
  <v-app dark>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title class="headline" v-if="error.statusCode === 404">
            {{ pageNotFound }}
          </v-card-title>
          <v-card-title class="headline" v-else>
            {{ otherError }}
          </v-card-title>
          <v-card-text>
            <p>
              <NuxtLink to="/">
                Home page
              </NuxtLink>
            </p>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>
