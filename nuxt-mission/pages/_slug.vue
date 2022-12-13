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
      <pre>{{ planet }}</pre>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const planet = await fetch(
      `https://api.nuxtjs.dev/planets/${params.slug}`
    ).then((res) => res.json())

    return { planet }
  },
}
</script>
