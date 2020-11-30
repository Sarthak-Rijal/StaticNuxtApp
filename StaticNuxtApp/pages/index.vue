<template>
  <p v-if="$fetchState.pending">Fetching Mountains...</p>
  <p v-else-if="$fetchState.error">An error occurred :(</p>
  <div v-else>
    <h1>Nuxt Mountains</h1>
    <ul v-for = "element of data">
      <img v-bind:src = "element.image"/>
      <li>{{element.title}} - {{element.height}}</li>
      <br>
      <li > {{element.description}}</li>
      <br>
      
    </ul>
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        data: []
      }
    },
    async fetch() {
      this.data = await fetch('https://api.nuxtjs.dev/mountains').then(res => res.json())
    }
  }
</script>