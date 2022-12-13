<!-- Please remove this file from your project -->
<template>
  <div
    class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0"
  >
    <h1>
      {{ $route.params.slug }}
    </h1>
    <div class="h-7 mx-auto sm:px-6 lg:px-8">
      <img :src="planet.image" alt="" />
      <h1>{{ planet.title }}</h1>
      <!-- <p v-if="$fetchState.pending">Fetching planets...</p>
      <p v-else-if="$fetchState.error">Error while fetchin planets...</p>
      <ul v-else> -->
      <!-- <li v-for="planet in planets" :key="planet.slug">
          <nuxt-link :to="planet.slug">{{ planet.slug }}</nuxt-link>
        </li> -->
      <!-- </ul> -->
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const planet = await fetch(
      `https://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => {
      if (res.ok) {
        return res.json()
      }
      throw new Error(res.status)
    })

    return { planet }
  },
  // data() {
  //   return { planets: [] }
  // },
  // async fetch() {
  //   this.planets = await fetch(`https://api.nuxtjs.dev/planets`).then((res) =>
  //     res.json()
  //   )
  // },
}
</script>
