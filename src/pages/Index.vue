<template>
  <q-page class="flex flex-center">
    <img
      alt="Quasar logo"
      src="~assets/logo.png"
    >
    <h1>{{ title }}</h1>
  </q-page>
</template>

<script>
export default {
  data: function () {
    return {
      title: 'Home'
    }
  }
}
</script>
