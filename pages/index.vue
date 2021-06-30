<template>
  <ul>
    <li v-for="content in contents" :key="content.id">
      <nuxt-link :to="`${content.id}`">
        {{ content.title }}
      </nuxt-link>
    </li>
  </ul>
</template>

<script>
export default {
  async asyncData ({ $microcms }) {
    const data = await $microcms.get({
      endpoint: 'column'
    })
    return data
  }
}
</script>
