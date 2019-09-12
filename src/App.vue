<template>
  <div id="app">
    <section class="section">
      <nav class="navbar is-spaced has-shadow">
        <div class="container">
          <input 
            type="text"
            @keypress.enter="search"
            v-model="searchQuery"
            class="input is-large"
            placeholder="What are you looking for?"
          >
          <a class="button is-info is-large" @click="search">Search</a>
          <a class="button is-danger is-large">&times;</a>
        </div>
      </nav>

      <div class="container results">
        <div class="columns">
          <div class="column" v-for="character in characters" :key="character.name">
            {{character.name}}
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
const characters = [
  { name: 'Luke', world: 'skywoker' }
]
export default {
  name: 'app',

  data() {
    return {
      searchQuery: '',
      characters: []
    }
  },

  methods: {
    search() {
       console.log(this.searchQuery)
      this.characters = characters.filter(character => character.name.search(this.searchQuery) > -1)
    }
  },

  components: {
  }
}
</script>

<style lang="scss">
  @import './scss/main.scss';
  .results {
    margin-top: 30px;
  }
</style>
